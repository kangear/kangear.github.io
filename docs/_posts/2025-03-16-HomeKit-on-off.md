---
layout: post
title:  "HomeKit通断器使用说明"
date:   2025-03-16 16:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 开始之前

可以根据图片确认配件是否齐全 

| ![](/assets/b02b9d0647ad2735a817d6a299c0a1d.jpg) |
| :------------: | 
|          配件全家福    |

# 测试配件

## 自身按键测试

按机身按钮可以正常摆臂，如果不能则说明需要充电，请充电后重新尝试

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/760a7b3f9cdbe30c764afe61b49d9df9.mp4#t=0.001" type="video/mp4">
</video>

## 配对圆形遥控

| ![](/assets/微信截图_20250218111826.png) | ![](/assets/ddf92f5c3acae072b3e654e43e73be2.jpg) |
| :------------: | :------------: |
|  圆形遥控  |  界面预览  |


# 配置USB伴侣

参照《[HomeKit配件使用说明][2]》，配置完毕之后会出现图所示：

| ![](/assets/d86024032717dc4ad7c7e968cf5b44f.jpg) | ![](/assets/ffb60bf5fc1a43d3ffce05542b7e723.jpg) | ![](/assets/fe5a2facd34daae3f2ed91c86dd3006.jpg) |
| :------------: | :------------: | :------------: |
|  界面预览  |  开关(按电梯中用不到)    |  Touch是用在电梯功能中   | 

## 将USB伴侣和机器人关联

和圆形遥控类似，需要长按机器人主机按键，蓝色指示灯闪亮，再按iPhone`苹果家庭`中新出现的`Touch`或者`开关`来配对。按一次，机器人主机指示灯闪一次，表示关联成功。然后多按几次直到手指机器人能被手机控制。下面是视频讲解：

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/52baa06876b128bbb611f70d51d23072.mp4#t=0.001" type="video/mp4">
</video>

# 按电梯\电脑开机 固定方法

这一步的目的是将机器人固定到电梯按钮处。

## 按电梯测试

先不用粘贴固定支架，使用手按在电梯按钮附近，并按按键看能否正常 按电梯，如果角度不对，力臂可以手动拨动调整

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/f8c7787dd566453266622f7ad1b0ce4d.mp4#t=0.001" type="video/mp4">
</video>

## 粘贴固定支架

使用3M胶将支架粘贴到上一步确定的位置处

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/4560d601648f2b8210507ea6ce0f6933.mp4#t=0.001" type="video/mp4">
</video>

## 测试连续按电梯

用手指在右侧力臂下来阻挡回弹角度，连续按按钮看能否保证`每次`都准确`按电梯`。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/35c53ea79e357e7cb4ebc2d3ba962362.mp4#t=0.001" type="video/mp4">
</video>

## 粘贴回弹胶垫

用手指在右侧力臂下来阻挡回弹角度，连续按按钮看能否保证`每次`都准确`按电梯`，如果不能保证每次按下电梯，则可以加高胶垫，由2个改为3个。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/8092d4bace0c2bbe19d3187ecc753707.mp4#t=0.001" type="video/mp4">
</video>

# 使用控制

`Touch`可以重命名为`电梯`。

1. 可以通过`家庭App`控制   
触摸黄色图标直接远程按电梯；

2. 可以通过`Siri`控制   
`Siri 打开电梯`

3. 通过`控制中心`控制


[1]: https://kangear.github.io/a/2025/02/12/HomeKit-Device-List
[2]: /a/2024/12/28/b.html