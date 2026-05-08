---
layout: post
title:  "HomeKit门铃使用说明"
date:   2025-03-06 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1. 开始之前

## 1.1 功能演示

<video width="320" height="450" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/ff589ee10ef1432bb412799ef03199f6_raw.mp4#t=0.001" type="video/mp4">
</video>

## 1.2 流程图

| [<img src="/assets/homekit_doorbell_1.png"/>](/assets/homekit_doorbell_1.png)|
| :------------: | 
|          流程图    |


# 2. 添加到苹果家庭

1. 参照《[HomeKit配件使用说明][2]》进行配置WiFi和添加（**重要**）
2. 配置的后半程`关键步骤`如下所示：

| ![](/assets/fc064b4fc9d713316bdfe8141334aca.jpg) | ![](/assets/98a7470c19e1d3a534e329a3d5f0f4d.jpg) |![](/assets/b970b672cede966a2fcd804f4c86657.jpg) |![](/assets/8af07dba0a378defcb24bb727065519.jpg) |![](/assets/4adde0caaba3b0cec39e80a672ff58a.jpg) |
|:----------: |:----------: |:----------: |:----------: |:----------: |
|  1   |   2   |    3   |    4   |   5   | 

# 3. 门铃按键匹配

<video width="320" height="450" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/8482a3a72224ef47f3c30ee5e1ce5a69.mp4#t=0.001" type="video/mp4">
</video>
此时，按下门铃按钮HomePod可以发现响声，iPhone、Apple Watch、Apple TV可以收到推送通知。

# 4. 安装必读

1. 请勿安袭在防盗门上，金属会减弱信号。
2. 您可以先关上门，在想要安装的位置测试之后，再撕开双面胶固定。
3. 固定方式：建议先擦净墙上的灰，然后贴上门铃并按住5秒以上，若担心粘用不牢固，可使用螺钉安装。(请参考说明书)

# 5. 常见问题

## 5.1 问题排查

按下任意门铃按钮指示灯会闪烁，可以用来判断能否正常接收信号

## 5.2 iPhone收不到通知？

### 5.2.1 未开通 家庭App 通知权限

从iPhone设置中找到**通知**，从**通知**中找到**家庭**，将通知权限全部打开。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/8c15851daae8359a5e9c002a2c413fd1.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/cdf029750efa25e3d5f91c14c64af55f.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/011bc89e4d3ecde1a21bfd4a51b7e460.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">3</div>
  </div>
</div>

### 5.2.1 可能打开了[勿扰模式]

## 5.3 偶尔收到不到？

门铃距离伴侣太远了，最远不超过10米

## 5.4 音量

目前响铃音量和音乐音量同一个，无法只单独调整响铃音量。如果需要调整音量大小，可以利用HomePod上触摸区域或者喊“Siri，音量减小”来进行调整。



[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html