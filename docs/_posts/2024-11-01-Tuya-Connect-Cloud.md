---
layout: post
title:  "对接涂鸦智能平台的三种方式"
date:   2024-11-11 12:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

一个网友咨询自己的原设备是Debian控制，想要对接到涂鸦平台，没有使用WiFi模组，这里就整理几种对接平台的方式。

| 方式 | 描述 | 备注 |
| ---: | :----: | :----: |
|  WiFi模组  | 最常用的方法，不过需要硬件改动 |  |
|  TuyaOS Link SDK  | 比如[Python版本][1]，可以很简单的集成起来 |   |
|  TuyaOS SDK for Linux  | 有点过时的方法 |   |
|  云云对接  | 需要设备云进行适配，可以完全不修改硬件 |   |

# WiFi模组

# TuyaOS Link SDK

For Python是三年前的版本，For Android已经脱离

| ![有帮助的截图](/assets/微信截图_20241101115737.png) |
| :----------------------------------------: |
|          *涂鸦平台云云接入*          |

# TuyaOS SDK for Linux
略

# 云云对接

| ![有帮助的截图](/assets/涂鸦平台云云接入.png) |
| :----------------------------------------: |
|          *涂鸦平台云云接入*          |


[1]: https://developer.tuya.com/cn/docs/iot-device-dev/Link-SDK-Python?id=Kb4xpt3d2flds