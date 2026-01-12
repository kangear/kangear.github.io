---
layout: post
title:  "HomeKit空调伴侣说明书"
date:   2026-01-12 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1. 开始之前

空调伴侣，代替原遥控器，可以理解为接入了HomeKit智能空调遥控器。实现了直接喊Siri就可以开关空调，可以定时开关，也可以在回到家之前提前打开空调，刚进家门就立即享受凉爽。

## 1.1 功能演示


| [<img src="/assets/wechat_2025-09-14_121537_087.png" width="300"/>](/assets/wechat_2025-09-14_121537_087.png)|
| :------------: | 
|          安装效果    |

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/950d211ae4f89d24f43c4f9e7a0d5a98.mp4#t=0.001" type="video/mp4">
</video>

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/c9e28578e28270895f62d71d1ef819fa.mp4#t=0.001" type="video/mp4">
</video>


## 1.2 确认配件齐全

| [<img src="/assets/4d280e7cb3f7bb431095b52bcb3a1c2.jpg" width="300"/>](/assets/4d280e7cb3f7bb431095b52bcb3a1c2.jpg)|
| :------------: | 
|          配件全家福    |

# 2. 添加到苹果家庭

1. 参照《[HomeKit配件使用说明][2]》进行配置WiFi和添加（**重要**）
2. 配置的后半程`关键步骤`如下所示：

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 23%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/2047a0fdad43ce3fdf903290cbc48fdc.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 23%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/a1d16c37d86dae7ac4b312eeeecb0bf5.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">添加后效果</div>
  </div>
  <div style="width: 23%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/8e6cc5cbb8d069fd1d5d98d0da110ada.jpg" alt="效果" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">空调主界面</div>
  </div>
  <div style="width: 23%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/c415fd3c2548a675d1290469f46d3837.jpg" alt="效果" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">风速和摆风</div>
  </div>
</div>

# 3. 识别空调型号

## 3.1 一键识别

需要借助原空调遥控器来实现，USB上的按键按下3秒松手，用遥控器对着空调伴侣按开关机，连续10次左右，这时可以通过手机尝试控制开关空调，调整温度如果能正常控制则说明已经识别到。如果完全不识别、或者识别成功但是无法控制可以尝试【手动选择品牌】方式

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/2ebfc5b0ef8fa7a265d58b9218baa323.mp4#t=0.001" type="video/mp4">
</video>

## 3.2 手动选择品牌

添加之后，进入到配件设置界面，找到串号长按复制，粘贴到Safari浏览器打开，这时会打开配件内置的设置界面，可以进行选择品牌和协议，如果某个协议能支持正常开机和关机，可以点击保存，切换回家庭App进行控制，如果制冷、制热、调温、风速、摆风都正常则算成功。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/WeChat_20250720201200.mp4#t=0.001" type="video/mp4">
</video>

# 4. 更多设置

## 4.1 语音控制

语言习惯的不同，Siri可以很好处理**Siri，关闭空调**关闭指令，我们常说的**Siri，打开空调**并不好使，通过测试说成**Siri，将空调设置为制冷**。使用一段时间后，Siri就会正常处理**打开空调**。

## 4.2 隐藏家庭摘要温度显示

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/WeChat_20250804112338.mp4#t=0.001" type="video/mp4">
</video>

# 5 常见问题

# 5.1 温度明显过高 (比如显示72度)

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/05981f71e602a044d75a368894d2373b.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">现象</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/7f407565218a65c638d62e1676884dfd.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">解决方案</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/7f407565218a65c638d62e1676884dfd.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">解决方案</div>
  </div>
</div>

[1]: /a/2025/07/08/HomeKit-AC-List.html
[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html