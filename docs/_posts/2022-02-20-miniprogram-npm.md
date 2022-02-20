---
layout: post
title:  "小程序使用npm安装依赖"
date:   2022-02-20 22:55:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

https://developers.weixin.qq.com/miniprogram/dev/devtools/npm.html

以上是原文，但是描述的不够通俗，按照我自己的理解写了一遍。

# npm安装第一个包
在`app.json`所在目录（比如miniprogram）下执行
```
npm install --save miniprogram-sm-crypto
```

# 构建一下
```
工具-> npm
```
本步骤目的是将`node_modules`中的依赖转成小程序能识别的`miniprogram_npm`目录。依赖打包时会打包进小程序。

# 引用测试
在`pages/index/index.js`中引用
```js
// 头部
const sm2 = require('miniprogram-sm-crypto').sm2
let point = sm2.getPoint() // 获取一个椭圆曲线点，可在sm2签名时传入

//
Page({
  // ...
  onLoad(e) {
    console.log(point);
  }
  //...
})
```
小程序启动后打印
```
{privateKey: "8e31605a7e1cd63a5a522d2b0e78c830b1c03febb657a21f4516564405da7ed4", publicKey: "04b66dbaca3517faae9384278aa24f7d768ad3d74b2adfb0c7…35925d0ff8d8507d3932aabeaccd7b475fa5b549625909745", k: BigInteger, x1: BigInteger}
```
引用成功。
