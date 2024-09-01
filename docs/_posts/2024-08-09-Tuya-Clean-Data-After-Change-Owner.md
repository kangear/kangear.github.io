---
layout: post
title:  "涂鸦平台 换人后清空定时数据"
date:   2024-07-17 22:36:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

需求背景，普通的消费者很介意买到二手设备，但是其实所有的产品都是二手的，这里是指经过测试后，比较经典的是“iPhone女孩”事件。

以上是背景，如何解决呢？如何知道换了用户了呢？单说Tuya平台是使用以下关键词搜索到了解决方案，这时特别的记录一下。

| ![有帮助的截图](/assets/微信截图_20240809152745.png) |
| :----------------------------------------: |
|          *4*          |


不过经过仔细研究，通过Google搜索出现的会现出跨界，图中并非通用，仅限于 门锁、猫眼等设备。


通用的方案也类似，不过是通过指令开启`【重置状态通知】`的，其中CMD是`0x34`，平台生成的库文件中的宏定义名称为`MODULE_EXTEND_FUN_CMD`，函数名称为`open_module_reset_state_serve`。