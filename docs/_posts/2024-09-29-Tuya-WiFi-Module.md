---
layout: post
title:  "如何烧录涂鸦WiFi模组？"
date:   2024-09-29 11:30:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

对接涂鸦平台时间一年有余，对其熟悉不少，在平台上购买模组对新手不够友好，必须加200元让平台帮忙烧录程序，其实程序大多是通用的。如果选择手动烧录，又得理解不少平台相关知识，比如`烧录授权`、`生产凭证`、`生产凭证确认`、`生产解决方案`、`3X-SO(R-1) 烧录工具`等等。

| ![有帮助的截图](/assets/微信截图_20240929161657.png) | ![有帮助的截图](/assets/微信截图_20240929162931.png) |
| :----------------------------------------: | :----------------------------------------: |
|          *涂鸦官方烧录架*          |          *ESP8266测试架*          |

为了赌气，我还真就购买过，只有一个小板+弹簧就卖75元，烧录的时候一般需要RST还需要自行拔插VCC，最终我使用的是淘宝上的这种[ESP8266测试架][1]。

目前已兼容如下型号：
WBR3
BP3L

其他型号也可以基于该板进行跳烧烧录
CBU

# 如何烧录

前期调试，如果淘宝上有现货可以购买，比如WBR3，那就不要在涂鸦官网购买，在淘宝商家购买的还有【程序+授权】，购买回来可以直接使用MCU对接。如果一些型号比较偏，淘宝上找不到卖家，可以购买 空交付，以下是完整流程。

## 购买【空交付】

| ![有帮助的截图](/assets/微信截图_20240929163859.png) |
| :----------------------------------------: |
|          *空交付*          |

## 测试是否带程序

如果`WBR3`购买回来，装到[ESP8266测试架][1]上，看TX指示灯是否会自动闪烁，这是模组在向MCU发送心跳包，如果有则说明使用空交付的价格购买到了带程序+授权的模组，可以跳过烧录过程。

## 生产凭证确认

从购买订单处找到订单附带的`生产凭证`，然后注册登录到[涂鸦智慧生产管理系统][2]，在`生产管理`-`工单管理`-`生产凭证确认`，看到的输入框中输入，然后按`确认`。需要解释一下，确实如此，烧录个样品居然使用了 生产管理系统，我刚接触的时候也很惊讶。这一步是为了下一步铺垫。

| ![有帮助的截图](/assets/微信截图_20240929165714.png) |
| :----------------------------------------: |
|          *生产凭证确认*          |

## 生产解决方案

这是一个软件的名称，可以在[涂鸦智慧生产管理系统][2]中搜索下载，下载之后登录再次输入`生产凭证`，切换到`烧录授权`，这里为什么使用`授权`而不是固件，因为实质是`固件+三元组信息`，所以一次性会烧录到模组中。

| ![有帮助的截图](/assets/微信截图_20240929165740.png) |
| :----------------------------------------: |
|          *云模组烧录授权平台*          |

## 烧录成功

烧录成功后就可以使用了。

[1]: https://item.taobao.com/item.htm?_u=tapc2b16510&id=641432390529&spm=a1z09.2.0.0.4d692e8d942UGn
[2]: https://pms.tuya.com/
