---
layout: post
title:  "Android系统是如何启动起来的？"
date:   2021-10-22 11:17:05 +0800
categories: android
typora-copy-images-to: ../asserts
typora-root-url: ../
---

Android启动顺序是 固化代码 -> 引导程序(Bootloader) -> 内核(kernel) -> 系统(Android)。我们一步一步来分析一下。第一步固化代码，顾名思义，是固化在CPU中的一小段代码，作用是启动「引导程序」，可以理解成「开天辟地」的角色，开天辟地之前天下一片混沌，CPU也是如此，固化代码两眼一抹黑，它唯一的工作是摸到「引导程序」递上交接棒，完成历史使命，就嗝屁了。正因它是两眼一抹黑，所以他不会去管最终要启动是Recovery还是Android10还是Android11一些杂事。

好，接下来是引导程序，英文叫Bootloader，简称BL。对，淘宝上卖二手手机商家说的解BL锁说得就是它。引导程序的工作初始化内存，启动内核。引导程序启动完内核后，就嗝屁了。

内核启动后，开始初始外部硬件，比如屏幕、相机、喇叭等等。初始完之后，启动系统，它并不会嗝屁，而是在幕后配合Android系统唱双簧。

系统启动时会显示启动动画、发送启动完成广播、显示App列表等等。App打开相机时，调用系统Api是双簧台前的角色，真正干活的是内核在后台。这就是系统的启动过程。

| Android       |   说明   |
| :-------------: | :------: |
| Android       |   系统   |
| kernel(Linux) |   内核   |
| Bootloader    | 引导程序 |
| 固化代码      | 固化代码 |


为了加深理解我们来对比一下邻居，Windows、MacOS和iOS。

固化代码，我们在Windows、MacOS和iOS上很少听到。因为Windows上相对单一都是Intel芯片，你的电脑我的电脑都是Intel没有不同，就没有人讨论；MacOS和iOS上因为相对比较封闭，也就没有讨论。

引导程序，Windows上可以理解为常常说的BIOS。

内核，在Android上是Linux，在Windows上是Windows NT，MacOS和iOS上是darwin。

系统，在Windows上是Windows，在Android上是Android，在MacOS上是Mac，iOS上是iOS。这几句像是废话其实干货后面，系统也可以是Qt，Ubuntu，Fedora，CentOS，当然这是嵌入式Linux。



| Win        | Android       |   说明   | Mac/iOS |
| :----------: | :-------------: | :------: | :-------: |
| Windows    | Android       |   系统   | Mac/iOS |
| Windows NT | kernel(Linux) |   内核   | darwin  |
| BIOS       | Bootloader    | 引导程序 |         |
|            | 固化代码      | 固化代码 |         |


去[Youtube](youtu.be/dNvlNFnTmjk)上看讲解。

