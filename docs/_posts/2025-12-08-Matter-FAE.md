---
layout: post
title:  "Matter配件常见问题"
date:   2025-12-08 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

Matter 是智能家居的通用连接标准。就像 USB 统一了电脑外设的接口一样，Matter 统一了智能家居设备之间的“语言”：不管哪个品牌、哪个平台，只要支持 Matter，就能互相连接、互相控制，不再被单一生态绑住。

Matter 里一般有三个角色：控制器、中枢、配件。为了说得明白，下面统一这样叫：控制器就是你的 iPhone，负责扫码添加和日常控制；中枢就是 HomePod，留在家里负责远程控制和自动化；配件就是要接进来的设备本身，比如插座、灯。下面不再用“控制器、中枢”这些生涩的词。

## 1. Apple Home 配置配件三步骤

| 步骤 | 英文 | 中文 | 说明 |
|:---:| --- | --- | --- |
| 1 | **Connecting...** | **连接中...** | iPhone 正在通过蓝牙搜索并连接附近配件，如果卡在这一步，则一般是配件未上电 |
| 2 | **Setting Up...** | **设置中...** | 正在建立配对并下发基础配置，如果卡在这一步，一般是HomePod和配件之间不互通 |
| 3 | **Adding to home...** | **正在添加到家庭...** | 正在把配件加入家庭并完成最后配置。 |

## 2. 报错以及解决方案

| 序号 | 英文 | 中文 | 解决方案 |
| :---: | --- | --- | --- |
| 1 | **Unable to Add Accessory**<br>Connect to a 2.4 GHz Wi-Fi network and try again. | **无法添加配件**<br>接入 2.4GHz 无线局域网并重试。 | iPhone 临时连接 2.4G WiFi 后再次尝试配置。 |
| 2 | **Unable to Add Accessory**<br>Pairing Failed | **无法添加配件**<br>Pairing Failed | 配置时配件重启会提醒这个，可以重新尝试，或者更换新的电源供电。 |
| 3 | **Unable to Add Accessory**<br>An unknown error occurred. | - | 可以重启 HomePod 和 iPhone 后尝试。 |
| 4 | **Unable to Add Accessory**<br>Accessory is not reachable. | **无法添加配件**<br>配件不可连接。 | 确保 HomePod 状态正常，未出现异常。 |
| 5 | - | **无法接入网络**<br>确保网络可覆盖配件，还原配件后再重新尝试添加到家中。 | 可以重启 HomePod 和 iPhone 后尝试。 |
| 6 | **Thread Border Router Required**<br>To pair this accessory, your home network must include a Thread Border Router. | **要求 Thread 边界路由器**<br>若要配对此配件，家庭网络必须包含 Thread 边界路由器。 | 字面意思。 |
| 7 | **Accessory Not Found**<br>You may need to restart your accessory before you can add it to your home. | - | 重启配件或者 iPhone。 |

## 3. 截图

<div style="display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 10px;">
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/04015b38837e2c300772a408bb08e6e3.jpg" alt="2.4G 提示" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">1号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/6c14badd736fe9ec86ae73ccc3a8a14f.jpg" alt="Pairing Failed" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/01448b717fb2d1e0fc8fd183f8e4c3cd.jpg" alt="无法接入网络" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">5号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/39839a91124d70f63aab85578069d2ff.jpg" alt="Thread 要求" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">6号</div>
  </div>
</div>

## 4. No response/未响应/沒有回應

4.1 添加上就显示【未响应】

- 可以等于10分钟后自动恢复，或者重启一下路由器恢复
- 连接的WiFi热点为Ap桥接导致
配- 件没有和中枢(HomePod、Apple TV)同一个WiFi名下，中枢访问不到该配件导致。可以新建空家庭添加来验证
- 根据提示【升级家庭底层架构】进行升级操作
- 中枢（HomePod）工作不正常，将HomePod重启即可（有实际客户案例）
- 看错旧设备，即已经恢复出厂重新添加，旧设备未删除将会一直呈现此状态
- 两个不同地理位置的房子共用同一个“家庭”

4.2 使用一段时间后【未响应】

- 配件未开机导致
- 配件连接Android手机热点导致
- 两个不同地理位置的房子共用同一个“家庭”，新购买HomePod添加后导致

## 5. 扫码以外的添加方式

1. Matter配件除了可以扫码添加，也可以发现附近Matter配件并手动输入二维码下方代码方式进行添加。
2. 在家庭App中扫码添加会比直接使用系统相机扫码成功率高。
3. 每次配对添加时将设备重启一下再进行，成功率会比较高。
4. Matter强制依赖IPv6，如果WiFi路由器没有开启会导致添加上就显示 未响应。

## 6. 清除iPhone中Matter配件缓存

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