---
layout: post
title:  "STLink Utils出现error occured during flash mass erase"
date:   2024-10-23 18:40:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

`STLink Utils`一直比较好用，最近有一个代码改动需要烧录的时候擦除Flash验证，使用Keil可以勾选`全片擦除`，但是使用`STLink Utils`却不行，会报如下错误：

| ![有帮助的截图](/assets/微信图片_20241023184256.jpg) |
| :----------------------------------------: |
|          *报错*          | 

手里的板子芯片是使用`离线烧录器`烧录过的，难不成是这个问题？搜索了一下解决了，随便找个文件烧录并勾选`Skip Flash Protection verification`，然后就可以成功擦除了。

| ![有帮助的截图](/assets/944b14b11e40265217597cad6f3bda1.png) |
| :----------------------------------------: |
|          *解决*          | 

具体是否和那个`离线烧录器`有关系，暂时不得而知，先记录到这个程度。但是因为Keil是可以的，所以心里有底应该是一个软件层面的锁定保护。

