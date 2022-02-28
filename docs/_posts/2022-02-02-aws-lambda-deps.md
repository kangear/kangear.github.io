---
layout: post
title:  "AWS的云函数lambda正确打开方式"
date:   2022-02-02 12:14:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---


`云函数`(AWS称为lambda)无论是阿里还是腾讯家的，基本依赖是最为令人头痛。而官方教程不出意外总是那么的晦涩难懂。一口气能列出多种新概念。还是自己总结的方法好用。以Python环境为例子：

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
