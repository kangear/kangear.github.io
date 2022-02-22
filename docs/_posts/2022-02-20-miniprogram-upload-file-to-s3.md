---
layout: post
title:  "小程序上传图片到s3"
date:   2022-02-20 22:55:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 小程序直接使用aws-SDK
根据[小程序使用npm安装依赖][1]开始安装，报了这个错误
```
module miniprogram_npm/aws-sdk/crypto.js is not defined
```
执行了如下执行还是没有解决问题
```
npm i crypto --save
```
再执行
```
npm uninstall crypto --save
npm i crypto-js --save
```
还是报错：
```
页面【pages/index/index]错误:
 Error: module "miniprogram_npm/aws-sdk/crypto.js" is not defined
    at require (VM832 WAService.js:35)
    at n (VM832 WAService.js:35)
    at __REQUIRE__ (index.js:5)
    at util.js:196
    at Object.func (util.js:19)
    at __REQUIRE__ (index.js:5)
    at util.js:7
    at Object.func (aws.js:1)
    at __REQUIRE__ (index.js:5)
    at ec2-2016-11-15.min.json:30198(env: macOS,mp,1.05.2111300; lib: 2.14.1)
```
暂未找到合适的解决方案。
```
1. aws_s3/miniprogram/node_modules/@types/duplexify/index.js: 未找到npm包入口文件
2. aws_s3/miniprogram/node_modules/@types/lru-cache/index.js: 未找到npm包入口文件
3. aws_s3/miniprogram/node_modules/@types/node/index.js: 未找到npm包入口文件
```
https://blog.csdn.net/gengyiping18/article/details/105276056


# 小程序后端使用aws-SDK

# 小程序前端使用http接口上传
https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/dev/HTTPPOSTForms.html

小程序sdk不适用，走uploadfile，post表单方式


[1]: https://kangear.github.io/cloud/2022/02/20/miniprogram-npm.html
