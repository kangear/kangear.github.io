---
layout: post
title:  "HomeKit可编程开关使用说明"
date:   2025-04-28 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1. 开始之前

可编程开关又叫无线开关、遥控、情景开关、场景开关、随意贴、便利贴、随手贴，是一个物理开关可以触发HomeKit中的场景和设备。

| [<img src="/assets/program_button.png"/>](/assets/program_button.png)|
| :------------: | 
|          原理    |

## 1.1 功能演示

### 1.1.1 控制灯光
<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/22d2a84ac7c2753de308c36fed2a4b7a.mp4#t=0.001" type="video/mp4">
</video>

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/WeChat_20250428150004.mp4#t=0.001" type="video/mp4">
</video>

### 1.1.2 控制HomePod播放不同背景音乐
<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/WeChat_20250428145946.mp4#t=0.001" type="video/mp4"> 
</video>


## 1.2 确认配件齐全

一个USB伴侣、一个无线按键开关

# 2. 添加到苹果家庭

1. 参照《[HomeKit配件使用说明][2]》进行配置WiFi和添加（**重要**）
2. 配置的后半程`关键步骤`如下所示：

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/feac6ccd7e79c840cbaf3125646b994.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/b0eec46b365b1d71733847946acb1f6.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">添加后描述不显示，需要从房间找到</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/92a4c3dab689d8d6327159d275a7455.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">按一下、连按两下、长按事件配置</div>
  </div>
</div>

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/1c652ce9fbed2eb752f9b39b5ee97f09.png" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">找到序列号复制并在Safari打开</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/dd18be9c2a49d039471b1992f2f5aacf.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">选择按键编号，按learn进行学习，这时可以按物理按键</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/b8033c01fa5a28faa4a5ef6716029e75.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">按test检测学习结果，像图上有数值代表成功</div>
  </div>
</div>

## 控制空调开关实例

结合空调伴侣，可以实现面板一键打开关闭空调，以下是配置过程演示

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/1fc502b535dd3b62c69241b04b62eccd.mp4#t=0.001" type="video/mp4"> 
</video>


[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html