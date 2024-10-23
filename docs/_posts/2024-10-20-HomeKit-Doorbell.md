---
layout: post
title:  "实现支持HomeKit的门铃"
date:   2024-10-20 01:20:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

和`HomeKit`相关的技术，先是接触了`Aqara M1S网关`、`涂鸦HomeKit方案`、`HomeBridge`，慢慢了解的更深入一点了。最近赶巧一个网友跑一个[门铃例子][1]的时候跑不起来，让我帮忙解决，我一看资料这不是我`心心念`的技术吗？就是基于ESP32的HomeKit。我还畅想了，如果有这种协议就好了，可以直连HomeKit，如果得来全不费功夫。

昨天闲来无事，决定把这个例子跑起来看看，看了资料是结构是这样的。

| 架构 |
| :----: |
|  doorbell  |
|  HomeSpan  | 
|  Arduino  | 
|  ESP-C3-12F  | 

我先使用`ESP32-WROOM-TesterBoard`结果一直运行不成功，最后改用`ESP32-C3-12F`测试通过了。

## 先看最终效果

| ![有帮助的截图](/assets/7201729359999_.pic.jpg)| ![有帮助的截图](/assets/7181729359995_.pic.jpg) | ![有帮助的截图](/assets/7191729359997_.pic.jpg) |
| :-------------------: | :--------------------------: | :--------------------: |
|          *模拟按下门铃*          |         *设备列表*          |        *即时通知*          |

## 从代码开始

首先说明，安装Arduino、ESP32开发板支持 和`HomeSpan`这里就不再赘述了，直接开始开始新建立工程，由于该Git仓库中代码工作是PlatformIO是对Arduino的再次封装，这次就不采用`他多大鞋，我多大脚`策略了，直接改为Arduino工程，以下是代码改进后的效果：
```cpp
#include <Arduino.h>

#include "Homespan.h"

// https://github.com/HomeSpan/HomeSpan/blob/master/examples/16-ProgrammableSwitches/16-ProgrammableSwitches.ino
struct Doorbell : Service::Doorbell // StatelessProgrammableSwitch
{
  SpanCharacteristic *switchEvent;

  Doorbell(int doorbellPin) : Service::Doorbell() // StatelessProgrammableSwitch
  {
    switchEvent = new Characteristic::ProgrammableSwitchEvent();

    new SpanButton(doorbellPin, 2000, 5, 200, SpanButton::TRIGGER_ON_HIGH);
  }

  void button(int pin, int pressType) override
  {

    switchEvent->setVal(pressType);
  }
};

int doorbellPin = 3; // 15 Board has no 15

void setup()
{
  Serial.begin(115200);
  homeSpan.begin(Category::ProgrammableSwitches, "Doorbell");
  homeSpan.enableWebLog();

  new SpanAccessory();
  new Service::AccessoryInformation();
  new Characteristic::Identify();
  new Doorbell(doorbellPin);
}

void loop()
{
  homeSpan.poll();
}
```

保险起见先注释掉代码，只留下一个HelloWorld，开始编译烧录，烧录按照[ESP32-C3烧录][2]方法。

| ![有帮助的截图](/assets/6eb4ffb8b4daa7c5c78b00cca4a5334.jpg) |
| :----------------------------------------: |
|          *配置和烧录*          | 

| ![有帮助的截图](/assets/7061729268530_.pic.jpg) |
| :----------------------------------------: |
|          *成功启动*          | 

## 配置WiFi

成功启动之后，我尝试使用Home App去配网怎么也发现不了设备，后来仔细看日志发现提示WiFi没有配置，采用串口输入命令的方式把WiFi配置成功了。

| ![有帮助的截图](/assets/7071729268664_.pic.jpg) |
| :----------------------------------------: |
|          *配网成功*          | 

| ![有帮助的截图](/assets/微信截图_20241023144240.png) |
| :----------------------------------------: |
|          *启动效果*          | 

## Home APP添加并试用

成功启动之后，根据串口提示现在已处于待配网状态。我尝试使用Home App去配网怎么也发现不了设备，后来仔细看日志发现提示WiFi没有配置，采用串口输入命令的方式把WiFi配置成功了。

| ![有帮助的截图](/assets/7091729359985_.pic.jpg) | ![有帮助的截图](/assets/7101729359986_.pic.jpg) | ![有帮助的截图](/assets/7111729359986_.pic.jpg) | ![有帮助的截图](/assets/7121729359987_.pic.jpg) | ![有帮助的截图](/assets/7131729359987_.pic.jpg) |
| :------------: | :------------: | :------------: | :------------: | :------------: |
|          *1*          |           *2*          |           *3*          |           *4*          |           *5*          | 

| ![有帮助的截图](/assets/7141729359989_.pic.jpg) | ![有帮助的截图](/assets/7151729359990_.pic.jpg) | ![有帮助的截图](/assets/7161729359992_.pic.jpg) | ![有帮助的截图](/assets/7171729359994_.pic.jpg) | ![有帮助的截图](/assets/7201729359999_.pic.jpg) |
| :------------: | :------------: | :------------: | :------------: | :------------: | 
|        *1*       |       *2*      |     *3*     |     *4*    |     *模拟按下门铃*    | 

试用是将GPIO3接到3.3V上。

## 总结

其实乐鑫官网也有HomeKit的实现，但是如果索要SDK，其会要求提供8位数字代码，也就是其实要求必须是申请过PIID的公司才可以。虽然我也写邮件申请了，但是没有了下文，通过本文的例子更深一步理解了8位数字代码的来源，原来只是类似早年间传统蓝牙配网的配网码，只是同者之间生成的。iPhone和设备之间，设备需要是在Apple官网注册过的才可以，不过这里开源环境下未认证配件完全不影响使用。在抖音、咸鱼、淘宝等平台分享技术，也会被动带来技术更新。

[1]: https://github.com/paulstraw/homekit-doorbell
[2]: https://kangear.github.io/cloud/2024/07/09/ESP32-C3-Burn.html
