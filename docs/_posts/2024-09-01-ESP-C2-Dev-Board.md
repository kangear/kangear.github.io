---
layout: post
title:  "ESP8684-DevKitM-1 v1.1输出乱码"
date:   2024-09-01 18:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 乱码

波特率改为比较特殊的`74880`才可以。

| ![有帮助的截图](/assets/a19de297d5c6294c5da58488ec815ac.png) |
| :----------------------------------------: |
|          *ESP8684-DevKitM-1 启动日志*          |

这个波特率说明藏得很深，链接在[这里][1]。

| ![有帮助的截图](/assets/微信截图_20240901190735.png) |
| :----------------------------------------: |
|          *波特率说明*          |


注：有些sscom不支持自定义波特率，需要从daxia.com中下载最新完整版本的sscom才可以。

# 固件下载

[这里][2]

需要说明的是，只有4M固件才支持`BLUFI`等蓝牙配网功能。

# 烧录

| ![有帮助的截图](/assets/72e2784777cb6f7e8c5c57c801dd275.png) |
| :----------------------------------------: |
|          *串口方式烧录*          |


[1]: https://docs.espressif.com/projects/esp-idf/zh_CN/v5.3/esp32c2/get-started/establish-serial-connection.html
[2]: https://docs.espressif.com/projects/esp-at/zh_CN/latest/esp32c2/AT_Binary_Lists/esp_at_binaries.html