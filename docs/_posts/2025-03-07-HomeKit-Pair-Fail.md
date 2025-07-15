---
layout: post
title:  "HomeKit USB伴侣配网添加不成功？"
date:   2025-03-07 00:25:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

HomeKit USB伴侣成功连网使用细分为三步，连上WiFi、家庭App添加、家庭App控制成功，现在分别以不同阶段来分析问题。

## 1.连接WiFi阶段

### 1.0 没有HomeSpan-Setup热点

1. 设备未上电，或者设备上电后指示灯未闪烁
2. 重新配置时，仅删除设备，并没有将设备恢复出厂

### 1.1未自动弹出WiFi配置界面

iPhone连接上配件热点`HomeSpan-Setup`后，没有自动弹出输入WiFi名字和密码的界面，需要点击WiFi感叹号，开启[自动登录]。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/ed43cb786850765932d7bcb6ce1cfd2.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">正常弹出配置界面</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/0450cf71df2b134490c55be082146aa.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">仍然在WiFi列表界面</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/d866387c57550024d2f41999089e43e.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">开启[自动登录]</div>
  </div>
</div>

### 1.2搜索不到WiFi

1. WiFi路由器需要开启2.4G WiFi热点
2. 如果使用iPhone热点作为WiFi，则需要开启【最大兼容性】
3. 拔掉重新上电，这样可以重新搜索（因为每次上电只搜索一次）

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/2c75de776b1064cf6004fa926e3a70e.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">WiFi列表</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/dc18f56c3fe84c24a180b16780958334.png" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">路由器开启2.4G WiFi</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/86dd864aed3ed9b76f0f5fcfeb063838.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">iPhone热点开启2.4G WiFi</div>
  </div>
</div>

### 1.3连不上WiFi

1. 密码错误，需要改为正确密码再次尝试
2. WiFi路由器的【无线模式】由`802.11ax(WiFi6)`改为`WiFi4/5(传统模式)`
3. 该热点密码加密方式不兼容，需要设置为`WPA/WPA2-PSK`
4. 该WiFi热点信道不支持，需要选择为兼容模式

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/20250307023601.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">现象:卡在这个界面</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/20250307152543.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">路由器-无线模式</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/41477f04453bba96c426724bbe412682.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">路由器-加密方式</div>
  </div>
</div>

## 2.家庭App添加阶段

家庭App添加不成功的话，一般是会是连接的WiFi是`访客网络`，iPhone和USB伴侣无法通过局域网通信导致，一般商场公共网络会有这种情况，或者家用路由器但是设置了隔离模式。一定要确保家庭中的HomePod和Apple TV处于开机状态，不能处于`未响应`，因为这两个家伙是`管家`，增加和删除设备必须它们`在场`。

### 2.0 一直转圈不出现设备

| [<img src="/assets/50e37be22d6a8943a7dafd2890fa21b.jpg" width="300"/>](/assets/50e37be22d6a8943a7dafd2890fa21b.jpg)|
| :------------: |
|          一直转圈    |

1. 手机没有连接WiFi，或者和【被添加设备】不是同一个WiFi名
2. 家中有两个中枢AppleTV和HomePod，其中AppleTV没有开机（真实用户实例）
3. 确保家中路由器管理App中可以查看到名为`ESP32`开头的设备正常连接上
4. 使用`Discovery-DNS-SD Browser`App扫描局域网中的所有HomeKit设备来定位问题

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 25%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/e06ff9787989a3a09d51c290287c62f.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">AppStore中下载该App</div>
  </div>
  <div style="width: 25%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/3613b86cc1f9ff9dac903b7bb70660c.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">2</div>
  </div>
  <div style="width: 25%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/cef5c7955144584aba44a0ef595d7a5.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">3</div>
  </div>
    <div style="width: 25%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/9abe4f0da3ea56c4d9c7702802e775c.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">湿度计例子</div>
  </div>
</div>

#### 2.0.1 路由器不支持HomeKit协议的案例

某用户摸索一个小时仍然无法在 `Home` App 中搜索到设备，随后使用 `Discovery - DNS-SD Browser` App 进行测试，如下图所示，仅能发现局域网中与`隔空投送`相关的服务。

上图中3中本应出现的`hap`协议完全未被发现，而 HAP（HomeKit Accessory Protocol）正是 HomeKit 所使用的协议，基于 mDNS 底层广播机制。这说明该用户的路由器可能屏蔽或禁用了 mDNS 协议。

他进一步尝试用另一台 iPhone 开启热点，绕过原有 Wi-Fi 网络进行连接，结果设备可以被正常发现并成功配对，验证了路由器为故障源头。

该用户使用的设备是运营商电信赠送的`Tewa-1006G`路由器。

| [<img src="/assets/9c76ebd5070ba50f71808d188466d83.jpg" width="300"/>](/assets/9c76ebd5070ba50f71808d188466d83.jpg)|
| :------------: |
|          搜索不到`hap`案例    |

### 2.1无法连接配件

现象如下图所示，解决方法是：iPhone的**WiFi关闭再打开**，重新添加即可。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/4059dd306e728e6c2eb4b41699ebc6d6.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">简体中文版</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/817e606c018dcdf2cbbfa7cf94a9dfcd.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">繁体中文版</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/6496f75b6c1459eab83711ea9ed0753f.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">正在连接...</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/6b668dcc7c6e41dc70b80a8c62fe1b1.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">解决方案</div>
  </div>
</div>


### 2.2设置代码不正确

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/微信图片编辑_20250314221104.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">简体中文版1</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/微信图片编辑_20250314221104.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">英文版</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/微信截图_20250322121548.png" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">正在连接...</div>
  </div>
</div>

可以进行`恢复出厂设置`来解决。

### 2.3正在连接...

| [<img src="/assets/微信截图_20250615030953.png" width="300"/>](/assets/微信截图_20250615030953.png)|
|  :------------: | 
|          这可能需要一些时间    |

1. 注意图片上已有提示`中枢无响应`，要么无中枢，要么就保证中枢不出现无响应。中枢是家庭中的`管家`，在添加新配件时需要保证`管家`知情，删除配件也是如此。
2. 如果卡在这里超时30秒，则需要通过`恢复出厂设置`来解决。


### 2.4选错设备

如果家中有米家、绿米设备，可能是同步兼容HomeKit协议的，也会被罗列出来。记住一个规律，一般新发现的设备是排第一个。

## 3.家庭App控制阶段

家庭App控制不成功，添加上直接就是 未响应，一般也是隔离导致。

<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/44fff0eaa45813bc2766b1c0998fa08.jpg" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">升级家庭底层架构</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/44fff0eaa45813bc2766b1c0998fa08.jpg" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">升级家庭底层架构</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/44fff0eaa45813bc2766b1c0998fa08.jpg" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">升级家庭底层架构</div>
  </div>
</div>

### 3.1第一次就【未响应】

1. 连接的WiFi热点为Ap桥接导致
2. 配件没有和中枢(HomePod、Apple TV)同一个WiFi名下，中枢访问不到该配件导致。可以`新建空家庭`添加来验证
3. 根据提示【升级家庭底层架构】进行升级操作
4. 中枢（HomePod）工作不正常，将HomePod重启即可（有实际客户案例）
5. 看错旧设备，即已经恢复出厂重新添加，旧设备未删除将会一直呈现此状态

### 3.2一段时间后【未响应】

1. USB配件未开机导致
2. USB配件连接Android手机热点导致
3. 

### 3.3转圈

1. USB配件距离路由器较远，信号较差
2. USB配件在金属内，比如电梯、铁棚

