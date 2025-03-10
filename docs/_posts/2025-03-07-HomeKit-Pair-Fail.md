---
layout: post
title:  "HomeKit USB伴侣配网添加不成功？"
date:   2025-03-07 00:25:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

HomeKit USB伴侣成功连网使用细分为三步，连上WiFi、家庭App添加、家庭App控制成功，现在分别以不同阶段来分析问题。

# 连接WiFi阶段

## 搜索不到WiFi

1. WiFi路由器需要开启2.4G WiFi热点
2. 如果使用iPhone热点作为WiFi，则需要开启【最大兼容性】

| ![](/assets/2c75de776b1064cf6004fa926e3a70e.jpg) |  ![](/assets/dc18f56c3fe84c24a180b16780958334.png) |  ![](/assets/86dd864aed3ed9b76f0f5fcfeb063838.jpg) |
| :------------: | :------------: |:------------: |
|   WiFi列表    |         路由器开启2.4G WiFi    |  iPhone热点开启2.4G WiFi |

## 连不上WiFi

1. 密码错误，需要改为正确密码再次尝试
2. WiFi路由器的【无线模式】由`802.11ax(WiFi6)`改为`WiFi4/5(传统模式)`
3. 该热点密码加密方式不兼容，需要设置为`WPA/WPA2-PSK`
4. 该WiFi热点信道不支持，需要选择为兼容模式

| ![](/assets/20250307023601.jpg) |  ![](/assets/20250307152543.jpg) |  ![](/assets/41477f04453bba96c426724bbe412682.jpg) |
| :------------: | :------------: |:------------: |
|   现象:卡在这个界面    |     路由器-无线模式   |  路由器-加密方式 |

# 家庭App添加阶段

家庭App添加不成功的话，一般是会是连接的WiFi是`访客网络`，iPhone和USB伴侣无法通过局域网通信导致，一般商场公共网络会有这种情况，或者家用路由器但是设置了隔离模式。

## 无法连接配件

现象如下图所示，解决方法是：iPhone的**WiFi关闭再打开**，重新添加即可。

| ![](/assets/4059dd306e728e6c2eb4b41699ebc6d6.jpg) |  ![](/assets/817e606c018dcdf2cbbfa7cf94a9dfcd.jpg) |  ![](/assets/6496f75b6c1459eab83711ea9ed0753f.jpg) | ![](/assets/6b668dcc7c6e41dc70b80a8c62fe1b1.jpg) |
| :------------: | :------------: |:------------: |:------------: |
|   简体中文版    |     英文版   |  繁体中文版 | 解决方案 |




# 家庭App控制阶段

家庭App控制不成功，添加上直接就是 未响应，一般也是隔离导致。

## 转圈

1. USB配件距离路由器较远，信号较差
2. USB配件在金属内，比如电梯、铁棚




## 未响应

1. USB配件未开机导致
2. USB配件连接Android手机热点导致
3. 


