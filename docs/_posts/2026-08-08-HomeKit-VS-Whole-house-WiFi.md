---
layout: post
title:  "HomeKit遇上全屋WiFi"
date:   2026-08-08 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

## 开始之前

HomeKit产品不像米家、涂鸦那种直接上云，它重点利用了局域网通信，作为中枢的HomePod如果无法在局域网中找到设备，则该设备就会离线（显示未响应、沒有回應、No Response）。恰恰现如今用户局域网已经处于荒废状态，因为家庭WiFi大多是手机连接WiFi之后直接连接互联网，所以没有人会在意局域网是否ok。有三种情况，如果家里只有一个WiFi，那么局域网荒废但是还能使用；如果家里有多个不同名字的WiFi，那么这种情况是最糟糕的，因为HomePod会自动跳WiFi 但是设备不会，就会导致设备离线；如果家里部署了“全屋WiFi”，整个网络抽风的时候会导致离线，全上Thread是可以解决问题，但是WiFi还是硬通货。

## 只有一个WiFi

如果运营商赠送的WiFi路由器，则会概率出现分配IP不在同一个网段导致设备离线，也会出现运营商定制的路由器固件裁剪掉部分功能，导致设备甚至无法正常添加上。使用HomeKit搜索App无法搜索到_hap_。解决方法是购买一个普通的WiFi路由器即可。

## 多个不同名字的WiFi

因为HomePod会共享iPhone已经连接的WiFi，iPhone如果已经连接A、B两个WiFi，HomePod会在某些时刻也从A切换到B，但是如果设备还是连接着A，就会导致设备离线。

## 全屋WiFi

全屋WiFi的理想是比较美好的，全屋使用同一个WiFi名字，尽管是多个节点。但是偶尔抽风时，也会导致这个局域网之间设备无法互通，最终导致设备离线。解决方法就是可以将HomePod和设备绑定到同一个节点，这样可以减少抽风时的离线情况。


<div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/c25cace5305c39274eef38c272ebef22.png" alt="截图1" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">路由器App上找到设备</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/0542e2502d5cb3421a6bd623f5dc1a83.png" alt="截图2" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">设置成手动选择节点</div>
  </div>
  <div style="width: 32%; text-align: center;">
    <div style="width: 100%; position: relative;">
      <img src="/assets/0542e2502d5cb3421a6bd623f5dc1a83.png" alt="截图3" style="width: 100%; display: block;" />
    </div>
    <div style="width: 100%; text-align: center; margin-top: 8px;">设置成手动选择节点</div>
  </div>
</div>