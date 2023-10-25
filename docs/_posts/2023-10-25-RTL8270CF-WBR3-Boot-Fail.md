---
layout: post
title:  "RTL8270CF (WBR3) 烧录后启动总是停在Fast connect profile is empty, abort fast connection"
date:   2023-10-25 17:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

实物图
![screenshot-20231025-204204|382x500](/assets/WechatIMG1085.jpeg)


```
== Rtl8710c IoT Platform ==
Chip VID: 5, Ver: 3
ROM Version: v3.0

== Boot Loader ==
Oct 20 2021:16:31:20

fwx SELE[ffffffff]
fw SELE Bitidx 0, fw1 valid 1, sn 0, fw2 valid 1, sn 1
fw1 USE, return sn 0

[20:34:27.815]收←◆
Boot Loader <==

== RAM Start ==
Build @ 13:03:51, Mar 10 2023

$8710c>
build mp_firmware @ Mar 10 2023 13:04:32 0x9b03d105
interface 0 is initialized
interface 1 is initialized

Initializing WIFI ...
[Driver]: The driver is for MP

[20:34:27.994]收←◆[FAST_CONNECT] Fast connect profile is empty, abort fast connection

WIFI initialized

init_thread(55), Available heap 0x19808
```

我的烧录配置是这样的：
![screenshot-20231025-204204|382x500](/assets/67c47ea6f08a45283f23d84443882d7d877be61c.png)

我现在不确定是烧录方式的问题，还是固件问题，我甚至使用demo程序也不行，偶尔会能启动起来，能正常启动提build time是最新的，只成功过一次，log显示到这里到底是出了什么错了呢？我应该从哪里排查呢？还请各位帮忙指点一下 。

这里提供一下正常启动的唯一一次日志信息：
![screenshot-20231025-204204|382x500](/assets/WX20231025-205628.png)



在IC原厂的提问链接：https://forum.amebaiot.com/t/rtl8270cf-wbr3-fast-connect-profile-is-empty-abort-fast-connection/2352
