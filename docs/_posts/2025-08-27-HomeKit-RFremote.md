---
layout: post
title:  "HomeKit万能433射频遥控使用说明"
date:   2025-08-27 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 开始之前

射频遥控一般是不需要对准的遥控器，常用在晾衣架、车库门上，频率上又分为433、315等，该产品可以学习原遥控器协议后来代替，并且可以接入到HomeKit使用iPhone HomeApp控制、Siri语音控制、CarPlay控制。


## 确认配件齐全

| [<img src="/assets/f1747d96c60217969cdeb8ca57e885c9.jpg" width="400"/>](/assets/f1747d96c60217969cdeb8ca57e885c9.jpg)|
| :------------: | 
|          配件全家福    |

# 添加到苹果家庭

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


# 学习

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

# 设置为点动模式

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/7d90a6268df28ad3ebb3a4bb63846b96.mp4#t=0.001" type="video/mp4">
</video>

设置完之后可能不会立即生效，可以把家庭App划掉再打开就会生效了。


[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html