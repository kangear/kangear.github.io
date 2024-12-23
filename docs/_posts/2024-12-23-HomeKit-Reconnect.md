---
layout: post
title:  "HomeKit重连机制"
date:   2024-12-23 12:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# HomeKit重连机制

HomeKit架构中有严格的主从意识，必须是`中枢`或者`iPhone`主动连接配件，反之则不行。如果配件重启了，则需要等待被连接，有几种途径会进行重连，`iPhone`重新打开`Home App`、`HomePod`上出现一些控制指令等等，这种是通用重连机制，自动重连速度也考验路由器的性能，或者在设备重启时自动关闭TCP连接。

## 未响应(No response)

Home App上出现这种提示，说明失去网络连接或者已被重置，当然也可以强制去控制，有时能控制成功。路由器使用的好一些，能解决出现未响应问题，而且在硬件上可以实现软关机，当被断电之后立刻主动关闭TCP长连接，可以能让HomeKit快速识别到已断开。

## 不支持(Not Supported)

Home App上出现这种提示，比如已发现的雨量计(Rain Gauge)、门铃(Doorbell)，特别是门铃在第一次添加时还可以使用，如果HomePod重启之后就永远不会连接该配件，可能已经在iPhone、HomePod代码中过滤到了这个类型配件。但是Apple并没有一棒子打死这种设备，如果搭配其他类型的服务一起作为一个配件还可以继续使用。

| ![有帮助的截图](/assets/93e57d455b7969705173b57a78b8bd0.jpg) |  ![有帮助的截图](/assets/918f093864be8b7e3214d6074cb69c8.png) | 
| :------------: | :------------: |
|          *门铃*    |         *雨量计*    | 

综上所述，HomeKit是入行快，做深并不快，水很深。




