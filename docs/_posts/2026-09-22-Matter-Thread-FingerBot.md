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

注意：如果以上方法无法进入让指示灯闪烁，可以插着充电线状态长按10秒，按够之后可以拔掉充电线。

## 4. 充电

充电过程中指示灯呼吸状态，充满之后指示灯长亮。

<video width="240" height="320" controls style="display: block; margin: 0 auto 16px;">
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/1ad741a4571be548649afa647052572e.mp4#t=0.001" type="video/mp4">
</video>

## 5. 设置运行模式（可选步骤）

需要下载`Thread Doctor`工具App进行调节参数。注意：该App仅为工具App，不修改参数可以不用下载安装，修改参数后可以卸载无需保留。

<table style="table-layout: fixed; width: 100%; border-collapse: collapse;" border="1">
  <tr>
    <td style="text-align: center;">
      <img src="/assets/c91e40d258c3c0230c8f48577118be2b.jpg" alt="有帮助的截图" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/013665795531c0dba7fc2c30e5dbc3e6.jpg" alt="有帮助的截图" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/ccc43c489d3d5297bdeaaf46ee7b99e0.jpg" alt="有帮助的截图" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/8f85c7ef22ad8c98d85a174926767b5e.jpg" alt="有帮助的截图" />
    </td>
  </tr>
  <tr>
    <td style="text-align: center;">Thread Doctor App</td>
    <td style="text-align: center;">主界面，按Scan进行扫描</td>
    <td style="text-align: center;">Thread devices栏下找到设备</td>
    <td style="text-align: center;">找到Configuration栏下的Mode进行修改</td>
  </tr>
</table>

模式说明

| 模式 | 解释 |
| --- | --- |
| Light Mode | 开关模式，默认为此模式 |
| Elevator Mode | 电梯模式，按下之后界面会自动回到关闭 |
| Light Mode (No Touch)  | 开关模式，同时禁用设备上自带触摸，可以减少误动作 | 
| Elevator Mode (NoTouch) | 电梯模式，同时禁用设备上自带触摸，可以减少误动作 |


## 6. 常见问题

[Matter配件常见问题][3]

[1]: /a/2025/07/08/HomeKit-AC-List.html
[2]: https://adafruit.github.io/Adafruit_WebSerial_ESPTool/
[3]: /a/2025/12/08/Matter-FAE.html
