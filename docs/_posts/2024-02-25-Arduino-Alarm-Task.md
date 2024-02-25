---
layout: post
title:  "Arduino实现定时任务"
date:   2024-02-25 20:50:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

经典的`Arduino UNO`是不带内部RTC，板载外部的RTC也不带，就得使用SoftRTC，我找了几个库够用，这里列举出来。

定时任务在物联网中很常见，比如定时开关机。虽然需要SoftRTC来实现，但是由于物联网一般都连接了互联网，可以实现频繁`授时`，这样误差也不会太大，如果再使用锂电池供电实现不断电使用，那就没有RTC什么事了。

# TimeAlarms 

https://www.pjrc.com/teensy/td_libs_TimeAlarms.html

| ![有帮助的截图](/assets/16247e66b3567e87e89e76448021096.jpg) |
| :----------------------------------------: |
|          *TimeAlarms*          |

# digital-clock

https://projecthub.arduino.cc/plouc68000/simplest-uno-digital-clock-ever-03c185

| ![有帮助的截图](/assets/微信截图_20240225210457.png) |
| :----------------------------------------: |
|          *digital-clock*          |
