---
layout: post
title:  "Matter空调伴侣使用说明"
date:   2026-05-25 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

## 1. 开始之前

空调伴侣，代替原遥控器，可以理解为接入了Matter智能空调遥控器。将家中的空调统一接入主流智能家居平台，包括Apple HomeKit、Google Home、Amazon Alexa、Aqara、HomeAssistant、Samsung SmartThings等。支持语音控制、远程操作、自动化场景和定时任务等功能。只需扫描Matter二维码一键添加，即可在多个平台享受无缝的智能家居体验。语音控制上可以直接喊Siri就可以开关空调，可以定时开关，也可以在回到家之前提前打开空调，刚进家门就立即享受凉爽。

### 1.1 功能演示


| [<img src="/assets/wechat_2025-09-14_121537_087.png" width="300"/>](/assets/wechat_2025-09-14_121537_087.png)|
| :------------: | 
|          安装效果    |

<div style="display: flex; flex-wrap: nowrap; justify-content: center; gap: 16px; overflow-x: auto; margin-bottom: 16px;">
  <video width="240" height="320" controls style="flex: 0 0 auto;">
    <source src="https://homekit.oss-cn-beijing.aliyuncs.com/950d211ae4f89d24f43c4f9e7a0d5a98.mp4#t=0.001" type="video/mp4">
  </video>
  <video width="240" height="320" controls style="flex: 0 0 auto;">
    <source src="https://homekit.oss-cn-beijing.aliyuncs.com/c9e28578e28270895f62d71d1ef819fa.mp4#t=0.001" type="video/mp4">
  </video>
</div>


### 1.2 确认配件齐全

| [<img src="/assets/4d280e7cb3f7bb431095b52bcb3a1c2.jpg" width="300"/>](/assets/4d280e7cb3f7bb431095b52bcb3a1c2.jpg)|
| :------------: | 
|          配件全家福    |

## 2. 添加到苹果家庭

1. 给空调伴侣上电，最好使用5V2A以上充电头（电源适配器）
2. 打开 苹果家庭App，扫描设备上的Matter二维码进行添加，配置的后半程`关键步骤`如下所示：

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/801c307a533db04596354d0a7ff753f2.mp4#t=0.001" type="video/mp4">
</video>

## 3. 识别空调型号

注：以下方法中如果复制序列号在Safari中打不开，白屏或者进入到了百度、Google搜索界面，可以粘贴后在地址前面添加一个`http://`，不过一般不需要。非常小概率打不开的情况下，可以通过路由器找到ESP开头设备的IP地址填写到Safari地址栏进行打开。

### 3.1 手动选择品牌方式

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/68c3bfc05b3907a6441734f908886351.mp4#t=0.001" type="video/mp4">
</video>

注：香港General品牌可以选择【富士通】，台湾三洋(Sanlux)品牌型号RCH开头可以选择【海信】。

### 3.2 一键识别方式

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/7843f57125a915071d1bdefbf0f10ba2.mp4#t=0.001" type="video/mp4">
</video>

### 3.3 学习按键方式

如果以上两种方式均不可以，还可以采用学习方式，这种方式不区分空调型号。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/0ebe5980265e75709ec0626dceff8ff6.mp4#t=0.001" type="video/mp4">
</video>

## 4. 更多设置

### 4.1 除湿、吹风模式

复制序列号在Safari打开，可以修改制热功能，将其映射为除湿、吹风等模式。

<div style="display: flex; justify-content: center; gap: 28px; margin-bottom: 16px;">
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/b5e12cdb7f985b5d9bb4b98c6105cae4.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">复制序列号</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/62603dc27635351b7723256ed57fb36c.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">高级设置界面</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/4bc944b3d68b1036119ac1a18c17fee9.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">修改制热(HomeKit中显示升温)对应的功能</div>
  </div>
</div>


### 4.2 语音控制

语言习惯的不同，Siri可以很好处理**Siri，关闭空调**关闭指令，我们常说的**Siri，打开空调**并不好使，通过测试说成**Siri，将空调设置为制冷**。使用一段时间后，Siri就会正常处理**打开空调**。

### 4.3 隐藏家庭摘要温度显示

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/WeChat_20250804112338.mp4#t=0.001" type="video/mp4">
</video>

## 5. 常见问题

### 5.1 温度明显过高 (比如显示72度)

<div style="display: flex; justify-content: center; gap: 36px; margin-bottom: 16px;">
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/05981f71e602a044d75a368894d2373b.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">现象</div>
  </div>
  <div style="width: 24%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/7f407565218a65c638d62e1676884dfd.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">解决方案</div>
  </div>
</div>

### 5.2 空调无反应

空调伴侣是遥控器原理，三颗白色LED这面对准空调，并且中间不要有遮挡。

| [<img src="/assets/fbd69b59263f4edc449c677892b19610.jpg" width="300"/>](/assets/fbd69b59263f4edc449c677892b19610.jpg)|
| :------------: | 
|          三颗白色LED这面对准空调    |

### 5.3 无法添加配件

| [<img src="/assets/16c2e0bf02d85de8388abbb3ff7f6541.png" width="300"/>](/assets/fbd69b59263f4edc449c677892b19610.jpg)|
| :------------: | 
|          无法添加配件    |

解决方案：重启iPhone后再次添加即可

### 5.4 未响应

| [<img src="/assets/7156f8c52d0403191b0aaa1b4064293a.jpg" width="300"/>](/assets/fbd69b59263f4edc449c677892b19610.jpg)|
| :------------: | 
|          HomePod感叹号    |

解决方案：将HomePod切到2.4G WiFi，如果出现感叹号，重启路由器即可

### 5.5 不支持

| [<img src="/assets/ca261b5322a3c63c8aca27f6e4d97ec2.png" width="300"/>](/assets/fbd69b59263f4edc449c677892b19610.jpg)|
| :------------: | 
|          不支持    |

解决方案：HomePod固件版本过低（比如18版本），升级后解决

### 5.6 上电闪烁不规律

正常闪烁

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/e695abe67d3894c45243b210732e3de5.mp4#t=0.001" type="video/mp4">
</video>

异常闪烁例子，一般是供电不足，需要更换充电头，一般插座自带USB口、5V1A充电头容易出现供电不足。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/701ce06032c145eb5edb8ab742aa1b19.mp4#t=0.001" type="video/mp4">
</video>

## 6. 恢复出厂

设备上的按钮`长按10秒钟`后松手，指示灯开始慢闪，即恢复出厂成功。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/30121b222bbf4fb2bc12e7ad36a381a5.mp4#t=0.001" type="video/mp4">
</video>

[1]: /a/2025/07/08/HomeKit-AC-List.html
