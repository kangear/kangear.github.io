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

| ![](/assets/2c75de776b1064cf6004fa926e3a70e.jpg){ width=33% } |  ![](/assets/dc18f56c3fe84c24a180b16780958334.png){ width=33% } |  ![](/assets/WeChatedd8dcb1dbc4311cf3bb9e43f64ad62d.jpg){ width=33% } |
| :------------: | :------------: |:------------: |
|   WiFi列表    |         路由器开启2.4G WiFi    |  iPhone热点开启2.4G WiFi |

## 连不上WiFi

1. 密码错误，需要改为正确密码再次尝试
2. 该热点密码加密方式不兼容，需要设置为`WPA/WPA2-PSK`
3. 该WiFi热点信道不支持，需要选择为兼容模式

| ![](/assets/20250307023601.jpg){ width=33% }|  ![](/assets/wpa_wpa2_psk.png){ width=33% } |  ![](/assets/wpa_wpa2_psk.png){ width=33% } |
| :------------: | :------------: |:------------: |
|   现象    |         密码错误日志打印   |  路由器中改变加密方式 |

# 家庭App添加阶段

家庭App添加不成功的话，一般是会是连接的WiFi是`访客网络`，iPhone和USB伴侣无法通过局域网通信导致，一般商场公共网络会有这种情况，或者家用路由器但是设置了隔离模式。

# 家庭App控制阶段

家庭App控制不成功，添加上直接就是 未响应，一般也是隔离导致。


