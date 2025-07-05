---
layout: post
title:  "HomeKit空调伴侣"
date:   2025-06-03 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 开始之前

空调伴侣，代替原遥控器，可以理解为接入了HomeKit智能空调遥控器。实现了直接喊Siri就可以开关空调，可以定时开关，也可以在回到家之前提前打开空调，刚进家门就立即享受凉爽。

## 功能演示

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/950d211ae4f89d24f43c4f9e7a0d5a98.mp4#t=0.001" type="video/mp4">
</video>

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/c9e28578e28270895f62d71d1ef819fa.mp4#t=0.001" type="video/mp4">
</video>

## 确认配件齐全

| [<img src="/assets/4d280e7cb3f7bb431095b52bcb3a1c2.jpg" width="300"/>](/assets/4d280e7cb3f7bb431095b52bcb3a1c2.jpg)|
| :------------: | 
|          配件全家福    |

# 添加到苹果家庭

参照《[HomeKit配件使用说明][2]》，配置的后半程`关键步骤`如下所示：

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/b2b872a7a1d88b39f85880fc8090129.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/e3ebf26d5a42d93c4fb95abb21467ec.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/a1594d3bf3fafacc5f415f3a442fd90.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">3</div>
  </div>
</div>

# 识别空调型号

需要借助原空调遥控器来实现，用遥控器对着空调伴侣按开关机，连续10次左右，这时可以通过手机尝试控制开关空调，调整温度如果能正常控制则说明已经识别到。

## 标准款

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/41b4c07e0e008fee82567c3e318f8a8d.mp4#t=0.001" type="video/mp4">
</video>

## 升级款

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/2ebfc5b0ef8fa7a265d58b9218baa323.mp4#t=0.001" type="video/mp4">
</video>

# 更多设置

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/a217cdc697a4e0da1e791e1169f8806.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">设置界面可以修改名称，方便语音控制</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/6e04d49a1b603b59dec3743edc9178d.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">喊[Siri，关闭空调]的效果</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/f19ac38d02d7eb5dfa07f85133fbe31.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">喊[Siri，将空调设置为制冷]的效果</div>
  </div>
</div>

# 语音控制

目前猜测是语言习惯原因，Siri可以很好处理[Siri，关闭空调]关闭指令，我们常说的[Siri，打开空调]并不好使，通过测试说成[Siri，将空调设置为制冷]。

# 拷贝&学习

对于无法支持的空调，空调伴侣上添加了一个学习(Copy)功能，可以Copy原空调遥控器的信号并记录下来，可以在Home App中使用开关来控制空调的开和关。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/1c1ac74db93a3617b5c3cf043a1381b4.mp4#t=0.001" type="video/mp4">
</video>

# 实测列表

采用的码库都说是`全空调`支持，以下根据买家反馈的实测表

| 编号| 空调型号                        | 遥控器型号      | HXD索引  | IRRemoteESP8266  | 米家 |
| :---:| :---------------------------  | :-------       | :-----   | :--------------- | :--------------- |
| 1  | 格力-悦雅[`KF-72LW`]             | YAP0F          | 0x033E   | KELVINATOR(18)   | -  |
| 2  | 美的-高能星[`KF-23GW/Y-IA(R3)`]  |  -             | 0x03F8   | COOLIX(15)       | -  |
| 3  | 美的-酷省电[`-`]                 | RN10L5(B2HS)/BG| -        | BOSCH144(15)     | -  |
| 4  | 飞歌PHILCO[`-`]                  |  YB1FA5       | -         |      YES        | -  |
| 5  | 三菱重工 MITSUBISHI HEAVY[`SRK50RE1/SRC50RE1`] |  RYD502A 034A| YES | -  | 三菱重工22 |
| 6  | 格力-清新风 [`KFR-120LW`]        |  -             | -        |               -  | -  |
| 7  | 格力-轻柔风 [`KFR-35GW`]         | YAP0F20        | YES      | 屏显X             | -  |
| 8  | 格力-冷静王II [`-`]              | YAP0FB3        | -        |               -  | -  |
| 9  | 美的-智弧 [`KFR-26GW/N8MJA3`]    | RN10LB(B2HS)/BG | -        |              -  | -  |
| 10 | TCL [`KFRd-26GW`]               | TCL(细长白色)   | -        |        TCL112AC  | -  |
| 11 | 美的-冷静星 [`KF-51LW/Y-PA400(D3)`] | RN08CA/BG    | -        |     COOLIX(15)  | -  |
| 12 | 美的 [`-`]                       | RN02A/BG       | -        |              -  | -  |
| 13 | 约克 [`YGCC-OF/VRF`]             | YGCC           | 关X      |     NO          | -  |
| 14 | 松下 [`窗机`]                    | ACXA75C21270    | YES     |     -           | -  |
| 15 | 美的[``]                         | Y502K           | YES     |     -           | -  |
| 16 | 美的-酷风风管机[`KFR-100T2W`]     | RN10J2(B2H)/BG-K| YES     |   -           | -  |
| 17 | 格力-凉之静[`KFR-26GW`]          | YB0FB2           | YES      |   -           | -  |
| 18 | 松下[`KFR-52LW` `CS-JE18FL1N`]   | -               | YES      |   -           | -  |
| 19 | 美的[``]                         | RN51F/BG        | YES      |   -           | -  |
| 20 | AUX-省电侠[``]                   | YKR-Q/051-AF     | YES      |   -           | -  |
| 21 | 三菱机电-雾之峰[`MSZ-GV2223-W`]    | ACH221 344E     | YES       |   - | ID:2997(1/45)  |
| 22 | AUX[``]                         | YKR-H/009       | 等反馈      |   -           | -  |
| 23 | 格力-润仕[``]                    | YAP0FB2          | 定向导风   |   -          | -  |
| 24 | 格力[`KRF-35GW`]                | YAP0F3           | YES      |   -          | -  |
 








[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html