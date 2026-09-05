---
layout: post
title:  "HomeKit手指机器人(触屏版)使用说明"
date:   2025-04-03 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1.开始之前

## 1.1 功能演示

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/a1e3fa3f50f3f2bed5500dc6a09ea4fd.mp4#t=0.001" type="video/mp4">
</video>

<video width="320" height="240" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/88ff9559d4b3ff56b24164f99eede8a2.mp4#t=0.001" type="video/mp4">
</video>

<video width="320" height="240" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/818a6e5a7f38aa90374236956b5cf72e.mp4#t=0.001" type="video/mp4">
</video>

## 1.2 流程图

| [<img src="/assets/touch_fingerbot.png"  width="600"/>](/assets/touch_fingerbot.png)|
| :------------: | 
|          流程图    |


## 1.3 确认配件齐全

可以根据图片确认配件是否齐全 

| [<img src="/assets/8841f8bfeb65bc77f06e037c18621a3.jpg"  width="400"/>](/assets/8841f8bfeb65bc77f06e037c18621a3.jpg)|
| :------------: | 
|          配件全家福    |

# 2.配置USB伴侣

参照《[HomeKit配件使用说明][2]》，配置的后半程`关键步骤`如下所示：

| ![](/assets/07d181abbf13df980f31e5e7897f511.png) | ![](/assets/cc2dbabb243afcd98b9d2489e4b266d.png) | ![](/assets/35138a967435d92852280a351c922d8.png) | ![](/assets/f04643aa8c0c136f2eaa1554277752e.png) |![](/assets/10c3231171287bcad7f128b0e17c7f9.png) |
| :-----: | :------: | :-------: |:-----: |:-----: |
|  1  | 2   |  3   | 4   | 5   |

# 3.实际安装案例

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 16px; margin-bottom: 10px;">
  <figure style="margin: 0; text-align: center;">
    <div style="aspect-ratio: 3 / 4; background: #f6f6f6; display: flex; align-items: center; justify-content: center; overflow: hidden;">
      <img src="/assets/c2b7faaa3247ec4f374c64e22a4b49d.jpg" alt="案例1" style="width: 100%; height: 100%; object-fit: contain; display: block;" />
    </div>
    <figcaption style="margin-top: 8px;">案例1</figcaption>
  </figure>
  <figure style="margin: 0; text-align: center;">
    <div style="aspect-ratio: 3 / 4; background: #f6f6f6; display: flex; align-items: center; justify-content: center; overflow: hidden;">
      <img src="/assets/4583aa821e408ada6eaefa1a9e338865.jpg" alt="案例2" style="width: 100%; height: 100%; object-fit: contain; display: block;" />
    </div>
    <figcaption style="margin-top: 8px;">案例2</figcaption>
  </figure>
</div>

注意事项：
1. 可以使用机身触摸按钮来测试是否灵敏，如果不灵敏可以微调位置、或者更换触脚上的双面胶

# 4.使用控制

如演示视频所示。

## 4.1 参数调整

可以进入到配件详情界面，找到序列号，复制之后在Safari中打开，就可以修改参数了。

## 4.2 不灵敏？

如果调整参数之后还不灵敏，可以考虑使用充电宝充着电，或者一根充电线连着就可以增强感应电，让触摸变得更准确灵敏。

## 4.3 实现连续触控两次

<video width="500" height="500" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/339c7fa4a827b814d37fbebb208cb189.mp4#t=0.001" type="video/mp4">
</video>

## 4.5 保护膜导致不灵敏

一个真实案例，用户在试过加长触控按下时长，连接充电线仍然会偶发不成功，最终证实将保护膜去掉就正常了。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 40%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/5796a3962d11c19fe640797adacff933.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">之前</div>
  </div>
  <div style="width: 40%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/f77e4625121a3fd58622bbd1d8657d4c.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">之后</div>
  </div>
</div>



[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html