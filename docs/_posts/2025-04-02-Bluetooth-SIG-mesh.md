---
layout: post
title:  "Bluetooth SIG mesh"
date:   2025-04-02 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---


最近又了解了mesh，这个无数次闯入的协议。前段时间量产了一个涂鸦彩灯，还是SIG mesh协议的，只是采购现成的模组量产，所以没有深究具体是怎么回事。原来SIG 是“中立”的mesh，和涂鸦mesh、米家mesh都不同。

如果找到了中立mesh，那么我这个“媒婆”又可以嫁接了，比如嫁接到HomeKit中。

# 几篇介绍

1. [蓝牙 Mesh（SIG）][1]
2. [Bluetooth mesh networking][2]
3. [ESP-BLE-MESH][6] （重点推荐，带有实践过程）

# 调试工具

mesh也有Nordic出的类似nRF Connect一样的调试工具，叫作[nRF Mesh][3]。也有[EspBleMesh Android App][4]和[Silicon Labs App][5]。

# 设备端Demo

1. 手上有一个`SIG Mesh`的涂鸦彩灯，但是在`Provison`的时候报错，看来可能并不完全规范
2. 想着使用ESP32轻易实现一个Mesh设备，结果发现没有那么容易，比如没有Arduino端的例子可用

## 涂鸦设备

能搜索到，但是`Provison`的时候报错

## ESP32 Mesh例子

[ESP-BLE-MESH][6]，目前只有IDF版本，需要自行编译。

## 淘宝上购买成品

搜索出现的都是米家、涂鸦，有可能非标准的mesh。

# 小结

其实还没有研究完，但是我觉得这会是一个漫长的过程，因为其中的术语很多。那我也阶段性做小结更新，mesh还可以涵盖一些运行不了Thread的蓝牙设备，由网关转换成HomeKit也会是一种形式的存在。但是Mesh似乎像是定格了一样，支持的设备种类并不多，不过也无关紧要。总归找到了一种“标准”来依靠，要比自定义的BLE协议更加稳妥。

[1]: https://developer.tuya.com/cn/docs/app-development/sigmesh?id=Ka5vdjp2tlb23
[2]: https://en.wikipedia.org/wiki/Bluetooth_mesh_networking
[3]: https://www.nordicsemi.com/Products/Development-tools/nRF-Mesh
[4]: https://github.com/EspressifApp/EspBLEMeshForAndroid/releases/tag/v1.0.0
[5]: https://www.silabs.com/developer-tools/bluetooth-mesh-mobile-app
[6]: https://docs.espressif.com/projects/esp-idf/zh_CN/v5.4.1/esp32/api-guides/esp-ble-mesh/ble-mesh-index.html