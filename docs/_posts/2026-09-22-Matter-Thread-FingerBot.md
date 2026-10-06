---
layout: post
title:  "Matter Thread 手指机器人"
date:   2026-09-22 09:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

## 1. 开始之前

Thread版本无需WiFi，支持接入Apple HomeKit、Google Home、Amazon Alexa、Aqara、HomeAssistant、Samsung SmartThings等。支持语音控制、远程操作、自动化场景和定时任务等功能。只需扫描Matter二维码一键添加，即可在多个平台享受无缝的智能家居体验。语音控制上可以直接喊Siri就可以开关USB设备，可以定时开关。

## 2. 中枢要求

| [<img src="/assets/95ee4ca45262f6454aec6c2979d5e486.png" width="500"/>](/assets/95ee4ca45262f6454aec6c2979d5e486.png)|
| :------------: | 
|         支持Thread的中枢（不完全统计）    |


## 3. 添加到Apple Home

长按按键10秒松手，设备会进入配网状态，指示灯闪烁。

<video width="240" height="320" controls style="display: block; margin: 0 auto 16px;">
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/a29276ecde96ab7ec5ce92dfba5373eb.mp4#t=0.001" type="video/mp4">
</video>

## 4. 充电

充电过程中指示灯呼吸状态，充满之后指示灯长亮。

<video width="240" height="320" controls style="display: block; margin: 0 auto 16px;">
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/1ad741a4571be548649afa647052572e.mp4#t=0.001" type="video/mp4">
</video>

## 5. 更新固件

连接电脑或者Mac可以更新固件，待补充

## 6. 设置运行模式

需要下载`Thread Doctor`工具App进行调节参数。

| [<img src="/assets/8f85c7ef22ad8c98d85a174926767b5e.jpg" width="300"/>](/assets/fbd69b59263f4edc449c677892b19610.jpg)|
| :------------: | 
|         Thread Doctor    |

| 模式 | 解释 |
| --- | --- |
| Light Mode | 开关模式，默认为此模式 |
| Elevator Mode | 电梯模式，按下之后界面会自动回到关闭 |
| Light Mode (No Touch)  | 开关模式，同时禁用设备上自带触摸，可以减少误动作 | 
| Elevator Mode (NoTouch) | 电梯模式，同时禁用设备上自带触摸，可以减少误动作 |


[1]: /a/2025/07/08/HomeKit-AC-List.html
[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html