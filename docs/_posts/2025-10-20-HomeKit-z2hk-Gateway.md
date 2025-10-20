---
layout: post
title:  "HomeKit Z2HK网关使用说明"
date:   2025-10-20 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1. 开始之前

基于Zigbee2MQTT改造而来，直接改成了Zigbee2HomeKit，将原本支持前者的Zigbee设备悉数直接支持为HomeKit。想用HomeKit产品，HomeAssitant比较重，单独设备又比较少，那就试试Z2HK网关吧。

## 1.1 功能演示


| [<img src="/assets/z2hk.png" width="600"/>](/assets/z2hk.png)|
| :------------: | 
|          架构图    |


## 1.2 确认配件齐全

略

# 2. 添加到苹果家庭

1. 参照《[HomeKit配件使用说明][2]》进行配置WiFi和添加（**重要**）
2. 配置的后半程`关键步骤`如下所示：
<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/bb396f6c6b39da5e16f21a7888547282.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">找到Z2HK Bridge网关</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/954738fb1954c95b863fb68945505e6f.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">复制序列号在Safari打开</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/46b53010f6cdc9e9db23684daed87804.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">进入配对状态，此时网关顶部指示灯会亮；这时可以将设备也置于配对状态，就会自动加入，设备加入后刷新界面会多一个设备，这时可以按 Save and Reboot来重启生效</div>
  </div>
</div>


# 3. 添加设备

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/066d97a96035d0e7682ed17c0100a308.png" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">找到Z2HK Bridge网关</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/a7ea15ae4c5c07dd79c872bd7fbc062e.png" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">复制序列号在Safari打开</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/9860f86d4b69f7259b6dc3a61503aa57.png" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">进入配对状态，此时网关顶部指示灯会亮；这时可以将设备也置于配对状态，就会自动加入，设备加入后刷新界面会多一个设备，这时可以按 Save and Reboot来重启生效</div>
  </div>
</div>


[1]: /a/2025/07/08/HomeKit-AC-List.html
[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html