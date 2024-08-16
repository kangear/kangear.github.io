---
layout: post
title:  "AT+CGATT失败的原因-卡没有流量"
date:   2024-08-16 22:36:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

在调试4G通信，使用AT指令执行`AT+CGATT=1`失败，回想几个月前经历过这个失败，检查后发现确实如此，卡没有流量了。

| ![有帮助的截图](/assets/d4066fd6ab61370754815953d416354.png) |
| :----------------------------------------: |
|          *4*          |

结论，4G通信好浪费流量，短短一个星期就消耗了5M还多的流量。