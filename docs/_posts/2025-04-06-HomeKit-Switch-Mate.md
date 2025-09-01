---
layout: post
title:  "HomeKit懒人开关使用说明"
date:   2025-04-06 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1. 开始之前

## 1.1 功能演示

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/bf3f1ee681b967f6aacfdf4fcecee39d.mp4#t=0.001" type="video/mp4">
</video>

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/48e2e0547e18cd1dfaac1dd9eee63f2d.mp4#t=0.001" type="video/mp4">
</video>

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/8022e8669bef343b33a2359bdc2bf63a.mp4#t=0.001" type="video/mp4">
</video>

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/bf3202d7ec742b333de078a9b84244a2.mp4#t=0.001" type="video/mp4">
</video>

## 1.2 确认配件是否齐全

可以根据图片确认配件是否齐全

| [<img src="/assets/b02b9d0647ad2735a817d6a299c0a1d.jpg" width="600"/>](/assets/b02b9d0647ad2735a817d6a299c0a1d.jpg)|
| :------------: | 
|          配件全家福    |

# 2. 测试配件

## 2.1 自身按键测试

按机身按钮可以正常摆臂，如果不能则说明需要充电，请充电后重新尝试

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/760a7b3f9cdbe30c764afe61b49d9df9.mp4#t=0.001" type="video/mp4">
</video>

## 2.2 圆形遥控测试

按下圆形遥控，机器人指示灯会亮，机械臂会摆动，则正常。

## 2.3 配置USB伴侣

1. 参照《[HomeKit配件使用说明][2]》进行配置WiFi和添加（**重要**）
2. 配置的后半程`关键步骤`如下所示：

| ![](/assets/50d23a40869d350bc7c9a6c0c9507f7.png) | ![](/assets/01a0b300b99a3db42efe39e32be2f15.png) | ![](/assets/cb5f3be7f96c962b7a3fd6839f7d065.png) | ![](/assets/054c340b745435c391ffbcb555cd933.png) |![](/assets/9a8385c97106dd882d03f31bfdfe9da.png) |
| :-----: | :------: | :-------: |:-----: |:-----: |
|  1  | 2   |  3   | 4   | 5   |

此时已经完成配置，可以直接使用。其中`电梯`是用来控制电梯，`灵动`是控制自动回弹的面板，`翘板`是控制普通的翘板开关面板。可以只使用适合自己模式，其他两个按钮隐藏即可。

# 3. 高级设置（可选）

如果以上功能已经正常，则不需要以下操作。

## 3.1 配对圆形遥控

| [<img src="/assets/ddf92f5c3acae072b3e654e43e73be2.jpg" width="600"/>](/assets/ddf92f5c3acae072b3e654e43e73be2.jpg)|
| :------------: |
|  配对圆形遥控  |

## 3.2 将USB伴侣和机器人关联

和圆形遥控类似，需要长按机器人主机按键，蓝色指示灯闪亮，再按iPhone`苹果家庭`中按钮来配对。按一次，机器人主机指示灯闪一次，表示关联成功。然后多按几次直到手指机器人能被手机控制。下面是视频讲解：

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/52baa06876b128bbb611f70d51d23072.mp4#t=0.001" type="video/mp4">
</video>


## 3.3 更新电池

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/4b690b41c6ebafaf9f2dafebbd2d8383.mp4#t=0.001" type="video/mp4">
</video>

## 3.4 充电

不支持`双C口`充电，需要使用随机附送的`A转C口`充电。充电时红色指示灯亮，充满时蓝色指示灯亮。

| [<img src="/assets/19b21ab12adf320251c26339a3a8b55.jpg" width="300"/>](/assets/19b21ab12adf320251c26339a3a8b55.jpg)|
| :------------: |
|  不支持双C口充电  |

[1]: https://kangear.github.io/a/2025/02/12/HomeKit-Device-List
[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html