---
layout: post
title:  "Arduino Zero小试牛刀"
date:   2023-11-11 17:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

购买截屏：
![购买截屏|382x500](/assets/WX20231111-170522.png)

硬件接口上确实兼容Arduino UNO，但是程序居然不兼容，我们基于UNO写的一个控制电机定时转动的代码，编译不过。报了一些`EEPROM.h`、`<MsTimer2.h`等等问题，按照认知，Arduino给人一种全兼容的，只是性能不同，确实只有`Blink`可以做到全兼容，其它很容易使用到AVR单片机专用库，就会导致不兼容。既然使用了C++来实现，仍然有兼容问题，也是比较不太理想的。

烧录Blink的过程
![烧录Blink的过程|382x500](/assets/WX20231111-165908.png)

按照研发人员所讲，从`Arduino UNO`换成`Arduino Zero`，几乎相当于重新开发一遍。这里做个记录，先放到一旁吃灰，以后需要32位单片机开发的时候再使用这个。


