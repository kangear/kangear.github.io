---
layout: post
title:  "HomeSpan配网"
date:   2024-11-03 12:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

很想把基于HomeSpan的小产品落地，简直是一种小而美，算是一个产品夹缝，可以卖给使用iPhone但是不使用Apple其他产品的人，以这个目标的消费都不胜其数。通过《[实现支持HomeKit的门铃][1]》的经验，HomeSpan的缺点是不无认证、无图形化配网，前者勉强可以接受，后者消费者完全没有办法独立使用。今天决定尝试一下"图形化配网"，果然可以行，等于一切环节都打通了，快速iPhone Home/Siri周边产品即可。

# 实现方法

只需要在代码中添加如下两行代码，即可实现：

```cpp
  homeSpan.setControlPin(2);
  homeSpan.enableAutoStartAP(); // auto start AP if factory-reset or first boot
```

# 配网流程

| ![有帮助的截图](/assets/0450cf71df2b134490c55be082146aa.jpg) | ![有帮助的截图](/assets/2af4ce7a5c2f9d8d545d5edaa7639bf.jpg) | ![有帮助的截图](/assets/4d8065c835c32a00ea48c0c7abe5201.jpg) | ![有帮助的截图](/assets/2c75de776b1064cf6004fa926e3a70e.jpg) |
| :------------: | :------------: | :------------: | :------------: |
|          *WiFi列表会多出一个热点*    |      *输入密码连接*    |  *打开WiFi弹窗*    |     *为模组选择WiFi*          |

| ![有帮助的截图](/assets/ed43cb786850765932d7bcb6ce1cfd2.jpg) | ![有帮助的截图](/assets/4d8a5222ecda1cb52b8bb51f61bffaa.jpg) | ![有帮助的截图](/assets/2e7b26586724e64d2bac8042152e081.jpg) |
| :------------: | :------------: | :------------: |
|          *填入密码，并提交(SUBMIT)*   |     *保持为空，直接保存(SAVE Settings)*    |      *提示完成*   | 


# Home App添加

这里就可以按照《[实现支持HomeKit的门铃][1]》方式进行添加。

# 小结

通过图形化配网，就再也不需要`串口工具`了，这个技术也可以走进千家万户，这里非常想要吐槽一句，HomeSpan的代码仓库中舍不得放一个截屏，全是文字描述，有时间一张截屏胜过一页文字；另外HomeSpan是借助了WiFi认证作为配网通道，让`热点配网`又变得好用了起来，尽管现在已是蓝牙配网的时代了。

[1]: https://kangear.github.io/cloud/2024/10/19/HomeKit-Doorbell.html