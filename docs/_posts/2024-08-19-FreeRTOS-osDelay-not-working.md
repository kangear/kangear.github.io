---
layout: post
title:  "FreeRTOS osDelay not working?"
date:   2024-08-19 18:00:00 +0800
categories: IoT
typora-copy-images-to: ../assets
typora-root-url: ../
---

main函数甚至使用了如下代码，都如标题那样没有Delay。

```c
	while(1)
	{
		osDelay(1 * 1000);
		LOG_INFO_TAG(TAG, "...");
	};

```

# 结论

我在`osKernelStart()`之前调用了一个使用FreeRTOS中的osDelay函数，因为内核都没有启动。
