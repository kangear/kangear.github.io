---
layout: post
title:  "ESP32 ping不通OpenWrt路由器?"
date:   2024-09-11 16:30:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

满心欢喜使用上了乐鑫官方模组，结果却出现了标题的问题，测试了ESP-C2、ESP-C3均有此问题，该路由器型号为`Xiaomi Mi Router WR30U`，刷机了`QWRT R23.6.1 / LuCI Master (git-23.141.16773-28dd4b3)`，该路由器在iPhone、Windows等待正常电子设备连接均正常，连接一些传统的ESP8266模组也是正常的。


| ![有帮助的截图](/assets/微信截图_20240911165836.png) |
| :----------------------------------------: |
|          *模组*          |

| ![有帮助的截图](/assets/4d2fecbbcee57ed557045c7b2027a86.png) |
| :----------------------------------------: |
|          *偶尔ping不通路由器*          |

这个问题刚开始表现现象是连接不上TCP，最终开始聚焦到DHCP、DNS等等，最后发现是连ping路由器ip都ping不通。观察了日志也没有看出个原由。我手里也没有多余的，其他的OpenWrt路由器可以方便交叉测试，这个问题只能先搁置在这里。

