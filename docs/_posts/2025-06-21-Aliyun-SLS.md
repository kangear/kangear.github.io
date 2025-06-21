---
layout: post
title:  "基于Aliyun SLS的云串口"
date:   2025-06-21 09:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 前言

单片机设备调试一般是使用`USB转串口`观察日志，对于偶发故障的还需要长期观察，而且还会占用一个电脑，结合这两个痛点做了一个`云串口`工具，可以采用`Web Tracking`方式把串口日志上传到`阿里云SLS`，日志上云之后，不仅可以常规的查询、下载，可以进行数据加工、数据可视化。

# SLS主要参数

```
region: "cn-hangzhou"
project: "serial-log"
logstore: "adc"

wifi_ssid: "APECBLUE"
wifi_passwd: "12345678"
mac_addr: "11:22:33:44:55:66"
```

# 控制台说明

| [<img src="/assets/微信图片_20250621192448.png" width="300"/>](/assets/微信图片_20250621192448.png)|
| :------------: |
|          AliYun SLS    |

# 高级

invalid query: line 1:10: function regex is not supported
invalid query: line 4:12: function to_int is not supported
syntax error error position is from column:10 to column:12,error near < r' >

能使用的例子
```
* | WHERE regexp_like(message, 'Stack (\\d+,){9}\\d+')
| extend nums = split(regexp_extract(message, 'Stack ((\\d+,){9}\\d+)', 1), ',')
| extend 
    num1 = cast(nums[0] as bigint),
    num2 = cast(nums[1] as bigint),
    num3 = cast(nums[2] as bigint),
    num4 = cast(nums[3] as bigint),
    num5 = cast(nums[4] as bigint),
    num6 = cast(nums[5] as bigint),
    num7 = cast(nums[6] as bigint),
    num8 = cast(nums[7] as bigint),
    num9 = cast(nums[8] as bigint),
    num10 = cast(nums[9] as bigint)
```