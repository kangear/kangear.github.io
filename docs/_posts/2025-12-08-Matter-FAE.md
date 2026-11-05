---
layout: post
title:  "Matter 常见问题"
date:   2025-12-08 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

## 1. Apple Home添加三步骤

| 步骤 | 英文 | 中文 | 说明 |
|:---:| --- | --- | --- |
| 1 | **Connecting...** | **连接中...** | iPhone 正在通过蓝牙搜索并连接附近配件。 |
| 2 | **Setting Up...** | **设置中...** | 正在建立配对并下发基础配置。 |
| 3 | **Adding to home...** | **正在添加到家庭...** | 正在把配件加入家庭并完成最后配置。 |

## 2. 报错以及解决方案

| 序号 | 英文 | 中文 | 解决方案 |
| :---: | --- | --- | --- |
| 1 | **Unable to Add Accessory**<br>Connect to a 2.4 GHz Wi-Fi network and try again. | **无法添加配件**<br>接入 2.4GHz 无线局域网并重试。 | iPhone 临时连接 2.4G WiFi 后再次尝试配置。 |
| 2 | **Unable to Add Accessory**<br>Pairing Failed | **无法添加配件**<br>Pairing Failed | 配置时配件重启会提醒这个，可以重新尝试，或者更换新的电源供电。 |
| 3 | **Unable to Add Accessory**<br>An unknown error occurred. | - | 可以重启 HomePod 和 iPhone 后尝试。 |
| 4 | - | **无法接入网络**<br>确保网络可覆盖配件，还原配件后再重新尝试添加到家中。 | 可以重启 HomePod 和 iPhone 后尝试。 |
| 5 | **Thread Border Router Required**<br>To pair this accessory, your home network must include a Thread Border Router. | **要求 Thread 边界路由器**<br>若要配对此配件，家庭网络必须包含 Thread 边界路由器。 | 字面意思。 |
| 6 | **Accessory Not Found**<br>You may need to restart your accessory before you can add it to your home. | - | 重启配件或者 iPhone。 |

## 3. 截屏

<div style="display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 10px;">
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/04015b38837e2c300772a408bb08e6e3.jpg" alt="2.4G 提示" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/2d4967b48e3f0946f06c0e8a6790d1f8.jpg" alt="2.4G 网络页" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/39839a91124d70f63aab85578069d2ff.jpg" alt="Thread 要求" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">5号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/f77d15e4ab1108f9a91b6964304565db.jpg" alt="中枢说明" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">5号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/01448b717fb2d1e0fc8fd183f8e4c3cd.jpg" alt="无法接入网络" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">4号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/6c14badd736fe9ec86ae73ccc3a8a14f.jpg" alt="无法添加配件" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2号</div>
  </div>
</div>

## 4. 扫码以外的添加方式

1. Matter配件除了可以扫码添加，也可以发现附近Matter配件并手动输入二维码下方代码方式进行添加。
2. 在家庭App中扫码添加会比直接使用系统相机扫码成功率高。
3. 每次配对添加时将设备重启一下再进行，成功率会比较高。
4. Matter强制依赖IPv6，如果WiFi路由器没有开启会导致添加上就显示 未响应。

## 5. 清除iPhone中Matter配件缓存

<div style="display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 10px;">
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/db75b44cd6d6e7f3fc593dd04634947f.jpg" alt="设置入口" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">设置->通用->Matter配件</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/c82d850c5f23c72c70305c1ade1deba2.jpg" alt="删除缓存" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">删除旧缓存</div>
  </div>
</div>

[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html