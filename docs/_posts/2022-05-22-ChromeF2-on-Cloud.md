---
layout: post
title:  "云上实现Chrome F2功能"
date:   2022-05-22 17:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

Chrome F12很强大（获取网页中的视频、图片、字幕），如何在服务器上用代码实现F12功能？

以获取Twitter视频字幕为例，讲解如何在服务器上执行Chrome F12功能，手机就可以调用了。

| ![有帮助的截图](/assets/chrome-dev-tools.png) |
| :----------------------------------------: |
|          *Chrome F12*          |

```Dockerfile
# 1. use ubuntu 18.04 as base image
FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

# defining user root
USER root

# OS update
RUN apt-get -y update

RUN apt-get install -y wget
RUN apt-get install -y build-essential

# 安装chrome
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | tee /etc/apt/sources.list.d/google-chrome.list
RUN apt-get -y update
RUN apt-get -y install google-chrome-stable

# Expose ports
EXPOSE 5000

# add file
ADD * /

# 下载npm，安装
RUN apt-get install -y npm python3 python3-pip
RUN npm install -g chrome-har-capturer
RUN pip3 install -r requirements.txt

ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8
ENV PYTHONUNBUFFERED 1

# Set the default command to execute
CMD ["cd /var/task/"]
CMD ["python3", "-m" , "flask", "run", "--host=0.0.0.0"]
#ENTRYPOINT ["google-chrome", "--remote-debugging-port=9222", "--headless", "--no-sandbox", "--disable-gpu"]

```

```python
# -*- coding: utf-8 -*-
import os
from flask import Flask, request
import tempfile
import json
import platform
import requests
import urllib.parse
from urllib.parse import urlparse
from haralyzer import HarParser

app = Flask("chrome")

CHROME_CMD = "google-chrome"
HAR_CAPTURER = "chrome-har-capturer"
print(platform.platform())
if (platform.platform().find("amzn2") != -1):
    CHROME_CMD = "google-chrome"
    HAR_CAPTURER = "chrome-har-capturer"
elif (platform.platform().find("macOS") != -1):
    CHROME_CMD = '"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"'
    HAR_CAPTURER = "/usr/local/bin/chrome-har-capturer"

os.system(CHROME_CMD + " " + " --remote-debugging-port=9222 --headless --no-sandbox --disable-gpu &")

USER_AGENT = '"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.83 Safari/537.36"'

def do_id(url):
    print("url: " + url)
    har_file = tempfile.NamedTemporaryFile(suffix=".har").name
    os.system(HAR_CAPTURER + ' -f -c -o ' + har_file + ' "' + url + '" -a ' + USER_AGENT + ' -g 10000')
    with open(har_file, 'r') as f:
        har_parser = HarParser(json.loads(f.read()))
    entries = har_parser.har_data["entries"]
    vtt_url = None
    for entry in entries:
        if entry['_resourceType'] == 'xhr':
            # print(entry)
            u = entry['request']['url']
            o = urlparse(u)
            if o.path.endswith(".vtt"):
                vtt_url = u
                break
    os.remove(har_file)
    if vtt_url is None:
        print("无CC字幕")
        return {
            'statusCode': 404,
            'body': {
                "web_url": url,
                "vtt_url": None,
                "vtt_content": None,
            }
        }
    response = requests.get(vtt_url)
    data = response.content.decode('utf-8', errors="replace")
    txt = None
    if response.status_code == requests.codes.ok:
        txt = data
        print(txt)
    return {
        'statusCode': 200,
        'body': {
            "web_url": url,
            "vtt_url": vtt_url,
            "vtt_content": txt,
        }
    }

@app.route('/')
def hello_world():
    # 启动google_remote_debug
    # 启动chrome-har-capturer
    url = request.args.get('url')
    print("url: " + str(url))
    url = urllib.parse.unquote(url)
    return do_id(url)

if __name__ == '__main__':
    '''
    入口程序
    '''
    url = 'https://twitter.com/NASA/status/1527757524405043206'
    res = do_id(url)
    print(res)
```

视频讲解：https://www.youtube.com/watch?v=JI6JpQk-rAk

代码：https://github.com/kangear/ChromeF12OnCloud
