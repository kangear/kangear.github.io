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

1. 准备原空调遥控器，确保其电池有电且能正常使用。（仅支持原厂原装遥控器）
2. 按住空调伴侣USB上的配对按键 3秒后松开，指示灯熄灭，进入学习/配对模式。
3. 将原空调遥控器对准空调伴侣，连续按压开关机键约10次（每次按下后等待遥控器信号发送完成）。
4. 操作完成后，指示灯常亮，通过手机App尝试控制空调：
  - 尝试开关空调；
  - 尝试调节温度。

5. 判断结果：
  - 如果手机能正常控制开关机和调节温度，则配对成功。
  - 如果完全无法识别，或虽识别但无法正常控制，请尝试使用【手动选择品牌】的方式进行配对。



<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/2ebfc5b0ef8fa7a265d58b9218baa323.mp4#t=0.001" type="video/mp4">
</video>

## 3.2 手动选择品牌

1. 配件添加成功后，进入该配件的设置界面。
2. 在设置界面中找到串号（序列号），长按串号进行复制。
3. 打开 Safari 浏览器，将复制的串号粘贴到地址栏并访问，此时会打开配件内置的Web设置界面。
4. 在内置设置界面中，选择品牌和协议。
5. 选择完成后，测试该协议是否支持正常开机和关机。
6. 若某个协议能正常支持开关机，点击保存。
7. 保存后，切换回手机的家庭 App（或对应智能家居App），对空调进行控制测试。
8. 判断成功标准：制冷、制热、调节温度、风速、摆风等功能均能正常控制，则配对成功。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/WeChat_20250720201200.mp4#t=0.001" type="video/mp4">
</video>

# 4. 更多设置

## 4.1 除湿、吹风模式

复制序列号在Safari打开，可以修改制热功能，将其映射为除湿、吹风等模式。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/b5e12cdb7f985b5d9bb4b98c6105cae4.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">复制序列号</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/dbb2f619c816b56eb75fb07897780e06.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">高级设置界面</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/1c6498b0ebfaec0427852ff78f3b2dad.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">修改Heat对应的功能</div>
  </div>
</div>


## 4.2 语音控制

语言习惯的不同，Siri可以很好处理**Siri，关闭空调**关闭指令，我们常说的**Siri，打开空调**并不好使，通过测试说成**Siri，将空调设置为制冷**。使用一段时间后，Siri就会正常处理**打开空调**。

## 4.3 隐藏家庭摘要温度显示

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/WeChat_20250804112338.mp4#t=0.001" type="video/mp4">
</video>

# 5. 常见问题

## 5.1 温度明显过高 (比如显示72度)

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

## 5.2 空调无反应

空调伴侣是遥控器原理，三颗白色LED这面对准空调，并且中间不要有遮挡。

| [<img src="/assets/fbd69b59263f4edc449c677892b19610.jpg" width="300"/>](/assets/fbd69b59263f4edc449c677892b19610.jpg)|
| :------------: | 
|          三颗白色LED这面对准空调    |

# 6. 恢复出厂

设备上的按钮`长按10秒钟`指示灯由闪烁到熄灭，即可恢复出厂。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/b98a5f7368f729e9e6152d88bc56bb44.mp4#t=0.001" type="video/mp4">
</video>

[1]: /a/2025/07/08/HomeKit-AC-List.html
[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html