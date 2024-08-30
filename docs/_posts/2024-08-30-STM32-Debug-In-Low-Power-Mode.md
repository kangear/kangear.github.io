---
layout: post
title:  "使用Under Reset Connect解决STM32 Sleep模式无法调试问题"
date:   2024-08-30 18:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

第一个STM32工程，代码中添加了Sleep的低功耗模式之后，`调试烧录`就特别困难，我自行摸索出来的方法是疯狂连续的按键，然后`ST-Link Utils`上点击的`Connect to Target.`，偶尔能识别到。这样效率非常低，还好只是后期的烧录。

这样使用了三个月大概，前几天使用`离线下载器`，居然每次都能识别和烧录，暗自感慨。时至今日，我也终于鼓足勇气在Google搜索栏打了`NRST stm32 stlink utils`最终找到方案，把`NSRT`接到`ST-Link`上，经过测试问题得以解决。

硬件连接如下，我只参考了`NRST`:

| ![有帮助的截图](/assets/bcdeef582fc9ddf8a31c4fc7c1d04a508e06519d_2_1035x322.jpg) |
| :----------------------------------------: |
|          *4*          |

来源：https://community.husarion.com/t/solved-debugging-with-st-link/565/4

关于`ST-Link Utils`的配置：

| ![有帮助的截图](/assets/4bddc23c6ae5289fa7c4d5dafd368f7.png) |
| :----------------------------------------: |
|          *3*          |

这样就可以像`离线烧录器`一样，每次都轻松识别。Keil MDK也同样好用。



