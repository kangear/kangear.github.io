---
layout: post
title:  "Arduino SoftSerial陷阱"
date:   2024-02-25 11:10:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

Soft让Apple赚的盆满钵满，但是Soft还是有缺点，比如在Arduino中的SoftSerial（软串口），会出现乱码，又不是全部乱码会让人以为程序有问题。所以SoftSerial只适合使用当Debug串口，不适合当通用串口。Arduino那么好用，却只有一个串口，真让人感到蛋疼。

10年前学习嵌入式编程时，视频解码中的硬解也比软解牛逼。

| ![有帮助的截图](/assets/微信截图_20240225111818.png) |
| :----------------------------------------: |
|          *SoftSerial陷阱*          |