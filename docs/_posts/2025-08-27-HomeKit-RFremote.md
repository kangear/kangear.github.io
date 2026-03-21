---
layout: post
title:  "HomeKit万能433射频遥控使用说明"
date:   2025-08-27 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1.开始之前

射频遥控一般是不需要对准的遥控器，常用在晾衣架、车库门上，频率上又分为433、315等，该产品可以学习原遥控器协议后来代替，并且可以接入到HomeKit使用iPhone HomeApp控制、Siri语音控制、CarPlay控制。


## 1.1 确认配件齐全

| [<img src="/assets/f1747d96c60217969cdeb8ca57e885c9.jpg" width="400"/>](/assets/f1747d96c60217969cdeb8ca57e885c9.jpg)|
| :------------: | 
|          配件全家福    |

# 2.添加到苹果家庭

1. 参照《[HomeKit配件使用说明][2]》进行配置WiFi和添加（**重要**）
2. 配置的后半程`关键步骤`如下所示：

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/3416d46fd67d565b221d9999ee1d453b.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/3416d46fd67d565b221d9999ee1d453b.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/3416d46fd67d565b221d9999ee1d453b.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">3</div>
  </div>
</div>


# 3. 学习（普通版）

添加之后，进入到配件设置界面，找到**序列号**长按复制，粘贴到**Safari浏览器**打开，这时会打开配件内置的设置界面，可以学习和测试。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/cfadc1156e5ac455aae222d747e3d49c.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/cfadc1156e5ac455aae222d747e3d49c.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/cfadc1156e5ac455aae222d747e3d49c.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">3</div>
  </div>
</div>

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/a29378a3d78a487c2be5853598a46b8f.mp4#t=0.001" type="video/mp4">
</video>

## 3.1 设置为点动模式

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/7d90a6268df28ad3ebb3a4bb63846b96.mp4#t=0.001" type="video/mp4">
</video>

设置完之后可能不会立即生效，可以把家庭App划掉再打开就会生效了。

# 4. 学习（Pro版）

适用于窗帘、晾衣架等长码。

学习遥控器按键
1. 长按小按键 3 秒松手，灯灭，进入学习  
2. 按遥控器目标键，灯快闪，表示收码成功
3. 灯慢闪时在家庭 App 点 Button XX 绑定；成功后灯常亮
注：慢闪超 10 秒未绑定则作废，需重学。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/2026-03-21_160949_293.mp4#t=0.001" type="video/mp4">
</video>

## 4.1 如何Siri控制

| [<img src="/assets/2026-03-21_161457_775.png" width="200"/>](/assets/2026-03-21_161457_775.png)|
| :------------: | 
|          配件全家福    |

比如按照上图进行了命名，直接喊Siri说**晾衣架上升**，Siri并不能识别，因为Siri会把这个识别成开关，要在前面加一个**打开**；如果不想那么啰嗦，可以创建一个场景名字就叫做**晾衣架上升**，然后里面的动作绑定一下这个按键的**开**，后续直接喊**晾衣架上升**就可以了。

## 4.2 上升5秒自动停止

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/2a4031d669f90c902245d5615f31d5b1.mp4#t=0.001" type="video/mp4">
</video>

[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html