---
layout: post
title:  "Arduino STM32druino"
date:   2024-03-03 17:50:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

关键字：`Arduino`、`Nucleo-64`、`STM32F103RB`

| ![有帮助的截图](/assets/微信截图_20240303180614.png) |
| :----------------------------------------: |
|          * 板子图片 *          |

| ![有帮助的截图](/assets/微信截图_20240303180322.png) | ![有帮助的截图](/assets/f8f6729114de691f89afd2013304bb0.jpg) |
| :----------------------------------------: | :----------------------------------------: |
|          * HelloWorld点灯 *          |          * 注意配置-F103RB *          |

默认调试串口是STLink虚拟的，使用串口助手连接“默认的D1D0”是接收到不数据的，因为那是Serial2。

| ![有帮助的截图](/assets/微信截图_20240304154255.png) | ![有帮助的截图](/assets/a3df58f1215c6eaea614d2800021e28.png) |
| :----------------------------------------: | :----------------------------------------: |
|          * 串口Demo *          |          * 串口名字 *          |


# PINOUT

| ![有帮助的截图](/assets/FT4S7MBJ98RBEZI.jpg) | ![有帮助的截图](/assets/F8VOF5RJ98RBEZH.png) |
| :----------------------------------------: | :----------------------------------------: |
|          * Arduino风格管脚 *          |          * 外围引脚 *          |

补充配置电路板
```
https://github.com/stm32duino/BoardManagerFiles/raw/main/package_stmicroelectronics_index.json
```


出现的问题

1. 

1. 