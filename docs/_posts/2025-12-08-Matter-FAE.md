---
layout: post
title:  "Matter 常见问题"
date:   2025-12-08 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

## 1. 清除iPhone中Matter配件缓存

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/db75b44cd6d6e7f3fc593dd04634947f.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">设置->通用->Matter配件</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/c82d850c5f23c72c70305c1ade1deba2.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">删除旧缓存</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/c82d850c5f23c72c70305c1ade1deba2.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">删除旧缓存</div>
  </div>
</div>

## 2. 连接2.4G WiFi再次尝试

说明该Matter配件不支持5G WiFi，需要iPhone临时连接到2.4G网络再添加。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/04015b38837e2c300772a408bb08e6e3.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/2d4967b48e3f0946f06c0e8a6790d1f8.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/04015b38837e2c300772a408bb08e6e3.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">3</div>
  </div>
</div>

## 3. Thread Border Router Required

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/39839a91124d70f63aab85578069d2ff.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/f77d15e4ab1108f9a91b6964304565db.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/39839a91124d70f63aab85578069d2ff.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">要求 Thread 边界路由器</div>
  </div>
</div>

iPhone 15 Pro Max不会出现以上提示，说明其已经支持Thread直接连接控制，像Matter Over WiFi一样；另外一台iPhone 11上会有这种提示，说明需要HomePod 或者 AppleTV作为中枢。

## 4. 无法接入网络、无法添加配件

配网过程中配件重启、配网失败等会出现如下提示，解决方案是将配件重启后重新扫码添加

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/01448b717fb2d1e0fc8fd183f8e4c3cd.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">无法接入网络</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/6c14badd736fe9ec86ae73ccc3a8a14f.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">无法添加配件</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/6c14badd736fe9ec86ae73ccc3a8a14f.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">无法添加配件</div>
  </div>
</div>

## 5. 扫码以外的添加方式

1. Matter配件除了可以扫码添加，也可以发现附近Matter配件并手动输入二维码下方代码方式进行添加。
2. 在家庭App中扫码添加会比直接使用系统相机扫码成功率高。
3. 每次配对添加时将设备重启一下再进行，成功率会比较高。
4. Matter强制依赖IPv6，如果WiFi路由器没有开启会导致添加上就显示 未响应。

[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html