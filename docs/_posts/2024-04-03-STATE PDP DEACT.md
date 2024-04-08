---
layout: post
title:  "SIM卡出现：STATE: PDP DEACT"
date:   2024-04-03 14:17:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

很多卡用着用着出现标题上的问题，今天意外发现不插SIM卡也会报这个错，先记录下来后续再进行补充。

调用`AT+CIPSTART`时串口回馈的错误：

```
[14:18:04.227]收←◆
STATE: PDP DEACT

CONNECT FAIL
```

估计类似手机上显示的 无SIM卡 状态，识别不良。

# 依据IMSI判断
今天测试过程中又发现，出现标题问题的同时，一般也会出现IMSI读取失败的问题，IMSI和IMEI不同，前者是SIM卡中的“身份证号”，后者是模组身份证号，一般可以通过IMSI读取成功与否判断问题所在，比如SIM卡槽没有焊接好之类的。