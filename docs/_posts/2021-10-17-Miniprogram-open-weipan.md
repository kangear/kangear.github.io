---
layout: post
title:  "微信小程序调用企业微盘"
date:   2021-10-17 23:23:05 +0800
categories: android
typora-copy-images-to: ../asserts
typora-root-url: ../
---

小程序开发者想通过「企业微盘」分享一个「教学视频」给自己的用户，尝试过三种方式。

# 方案A: 像跳微店小程序一样跳到对应目录

因之前跳转过`微店`,可以直接跳到`商家主页`，这里也使用相同的思路。测试结果是跳小程序方式行不通，经过测试结果是跳到了用户自己的网盘，而无法跳到指定路径，网上没有相关资料。此方案不通。

# 方案B: 网页版

比如分享的文件链接：https://drive.weixin.qq.com/s/sdfsdfsf
调试版本小程序可以，但是无法添加到【业务域名】，直接在小程序内打开行不通。不过，经过测试可以在[客服]聊天窗口打开链接，所以可以设置关键字回复的方式。

| ![有帮助的截图](/assets/Selection_087.png) | 
|:--:| 
| *添加业务域名失败截图* |



# 方案C: 文字链接

比如分享的文字链接(#小程序://企业微盘/企业微盘/sfsd23fswf)
暂时对这种文字链接了解不多，没有相关资料，不过经过测试，可以在[客服]聊天窗口打开链接，所以可以设置关键字回复的方式。


# 相关测试代码
```js
  openShareWeipan: function(e) {
    // 方案A: 跳小程序方式行不通，跳到了用户自己的网盘
    //        无法跳到指定路径，网上没有相关资料
    // wx.navigateToMiniProgram({
    //   appId: 'wx92e25c25a75c927a',
    //   // path: 'page/sfsd23fswf',
    //   extraData: {
    //     foo: 'bar'
    //   },
    //   success(res) {
    //     // 打开成功
    //   }
    // })

    // 方案B: 网页版 (https://drive.weixin.qq.com/s/sdfsdfsf)
    // 调试版本可以，但是无法添加到【业务域名】，所以失败
    // 可以在[客服]聊天窗口打开链接
    wx.navigateTo({
      url: '/pages/webview/webview',
    })

    // 方案C: 文字链接(#小程序://企业微盘/企业微盘/sfsd23fswf)
    // 可以在[客服]聊天窗口打开链接
  },
```
