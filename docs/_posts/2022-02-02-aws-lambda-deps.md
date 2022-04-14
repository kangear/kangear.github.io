---
layout: post
title:  "AWS的云函数lambda正确打开方式"
date:   2022-02-02 12:14:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---


`云函数`(AWS称为lambda)无论是阿里还是腾讯家的，基本依赖是最为令人头痛。而官方教程不出意外总是那么的晦涩难懂。一口气能列出多种新概念。还是自己总结的方法好用。以Python环境为例子：


# 一阶
麻烦在于使用了一个`itunes-iap`模块， 需要按照 AWS 官方文档创建个部署包。
具体步骤是：

实现`lambda function`的文件叫`lambda_function.py`，而且此文件得存在于`<code_dir>`文件夹的根
```shell
cd <code_dir>
# 生成requirements.txt
pip install pipreqs && pipreqs .
# 安装依赖到本目录
pip install --target . -r requirements.txt
# 压缩
zip -r ../r01.zip * -x "venv/*"
```
然后把打包生成的 r01.zip 通过 Lambda Console 上传发布即可。

来自：https://www.jianshu.com/p/e78d9b4aa796

让`API Gateway`有多远就滚多远，使用`AWS-SDK`可以直接`invoke`云函数。或者有一天，我了解了前者，就不会让它滚。但是现在就是月多远就滚多远！

# 二阶
当我用上`google cloud`相关依赖，问题不断出来，类似如下的：
```
AWS lamba No module named 'google.protobuf'
Unable to import module 'lambda_function': cannot import name 'cygrpc' from 'grpc._cython'
```

原因`google protobuf`和`protobuf`有点近亲，让人混淆，前者被装到`lib64`目录下了，导致怎么打包都不行，都会报错找不到。`cygrpc`是必须打包环境和`lambda`环境完全一致`AMZN2+Python3.8`，复杂的函数不能使用3.7和3.9，因为前者环境不好找，后者EC2上不好装，装也是第三方，会有不兼容的情况。其实按照二阶段方法，还更好用了，至少代码目录没有那么乱了。依赖合成子目录，其实可以写一个`PyCharm`插件来实现打包和上传。

以下是完整步骤：
## AMZN2+Python3.8
使用Google Cloud的sdk一定要在以下环境上打包，否则会出现各种奇怪的依赖问题。因为有些深的库，兼容性会差一些。
```shell
sudo amazon-linux-extras install python3.8
```

## venv
```shell
pip3 install virtualenv && virtualenv -p python3.8 venv
source venv/bin/activate
```

## 安装依赖
```shell
pip install -r requirements.txt --upgrade
```

## test
```shell
python lambda_function.py
```

## 一键zip
```shell
cd venv/lib/python*/site-packages && zip -r ../../../../my-deployment-package.zip . && cd -
cd venv/lib64/python*/site-packages && zip -gr ../../../../my-deployment-package.zip * && cd -
zip -g my-deployment-package.zip *.py *.json

# 传到本地
sz my-deployment-package.zip

# 上传
aws lambda update-function-code --function-name MyLambdaFunction --zip-file fileb://my-deployment-package.zip
```

# 三阶
## Create the Lambda FFmpeg layer
```shell
wget https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz
wget https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz.md5
md5sum -c ffmpeg-release-amd64-static.tar.xz.md5
tar xvf ffmpeg-release-amd64-static.tar.xz
```

```shell
mkdir -p ffmpeg/bin
cp ffmpeg-4.3.1-amd64-static/ffmpeg ffmpeg/bin/
cd ffmpeg
zip -r ../ffmpeg.zip .
```
来自：https://aws.amazon.com/cn/blogs/media/processing-user-generated-content-using-aws-lambda-and-ffmpeg/

同样也可以创建`pget`的

## pget layer
```shell
wget https://github.com/Code-Hex/pget/releases/download/v0.1.1/pget_0.1.1_Linux_x86_64.tar.gz
tar xvf pget_0.1.1_Linux_x86_64.tar.gz
```

```shell
mkdir -p pget1/bin
cp pget_0.1.1_Linux_x86_64/pget pget1/bin/
cd pget1
zip -r ../pget1.zip .
```
不好用，复杂一点的网址就报错。

## axel
不成功

## aria2
```shell
wget https://github.com/q3aql/aria2-static-builds/releases/download/v1.36.0/aria2-1.36.0-linux-gnu-64bit-build1.tar.bz2
tar xvf aria2-1.36.0-linux-gnu-64bit-build1.tar.bz2
```

```shell
mkdir -p aria2/bin
cd aria2-1.36.0-linux-gnu-64bit-build1
cp aria2c ca-certificates.crt ../aria2/bin/
cd ../aria2
zip -r ../aria2.zip .
```
### 使用注意
```python
cmd = /opt/bin/aria2c --check-certificate=false https://example.com/1.mp4 -d / -o /tmp/1.mp4
os.system(cmd)
```
其中
1. ` --check-certificate=false`不验证书
2. `-d /`如果没有这个会报错，因为lambda fs是只读的

## youtube_dl
```shell
mkdir -p youtube-dl/bin
cd youtube-dl/bin
wget https://youtube-dl.org/downloads/latest/youtube-dl youtube-dl/bin/
cd ../
zip -r ../youtube-dl.zip .
```

## tor
```shell
mkdir -p tor/bin
cd tor/bin
wget https://raw.githubusercontent.com/qrtt1/aws-lambda-tor/master/tor
cd ../
zip -r ../tor_aws_lambda_layer.zip .
```

## google-chrome
```shell
https://github.com/shelfio/chrome-aws-lambda-layer

arn:aws:lambda:us-west-2:764866452798:layer:chrome-aws-lambda:25
```
