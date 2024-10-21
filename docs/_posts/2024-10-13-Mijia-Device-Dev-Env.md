---
layout: post
title:  "小米米家设备端开发"
date:   2024-10-13 13:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 前言

本篇和《[米家插件开发环境搭建][1]》形成姊妹篇，但是类似英语学习中的`听说`一样，看似很近其实也相差很遥远，无需同步理解，可以把设备开发理解为`听`，可以完全`不会说只会听`。如果想要快速对接一个设备，本篇是第一步，真正需要量产的时候才可能需要`插件开发`。如果没有自己的插件，那怎么开发设备端呢？以`MCU+WiFi`为例子，可以购买一个竞品设备，然后通过串口抓取通信协议，一般不超过10条指令，然后在淘宝上购买小米模组进行通信开发即可。这个过程中，无需注册小米IoT开发者账户、无需下载米家Beta App、简单快速的体验小米物联网下位机开发流程。

# 小米智能模组

[MHCWB5S-B][2]


[1]: https://kangear.github.io/cloud/2024/10/12/Mijia-Plugin-Dev-Env.html
[2]: https://item.taobao.com/item.htm?_u=lapc2b1ace1&id=748875413031&spm=a1z09.2.0.0.2b102e8dLTIABS&skuId=5490368429797