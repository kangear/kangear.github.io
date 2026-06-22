---
layout: post
title:  "HomeKit配件添加到Home Assistant中"
date:   2026-03-29 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 1. 开始之前

如果设备已经添加到 iPhone「家庭」，则无法被 Home Assistant 发现或接入，需要先恢复出厂。

## 1.1 恢复出厂

长按设备按钮`约10秒`，待指示灯由闪烁变为熄灭，即完成恢复出厂。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/b98a5f7368f729e9e6152d88bc56bb44.mp4#t=0.001" type="video/mp4">
</video>

## 1.2 配置WiFi

<table style="table-layout: fixed; width: 100%; border-collapse: collapse;" border="1">
  <tr>
    <td style="text-align: center;">
      <img src="/assets/0450cf71df2b134490c55be082146aa.jpg" alt="有帮助的截图" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/2af4ce7a5c2f9d8d545d5edaa7639bf.jpg" alt="有帮助的截图" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/4d8065c835c32a00ea48c0c7abe5201.jpg" alt="有帮助的截图" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/2c75de776b1064cf6004fa926e3a70e.jpg" alt="有帮助的截图" style="width: 100%;" />
    </td>
  </tr>
  <tr>
    <td style="text-align: center;">iPhone中会多一个WiFi热点<code>HomeSpan-Setup</code></td>
    <td style="text-align: center;">输入密码<code>homespan</code>连接(可选步骤)</td>
    <td style="text-align: center;">按<code>下箭头</code>打开WiFi弹窗*</td>
    <td style="text-align: center;">为设备选择<code>家里WiFi</code>，这里以<code>QWRT-2.4G</code>为例</td>
  </tr>
</table>

**关于特殊WiFi**：
1. 访客WiFi：不要使用，HomeKit原理是局域网通信，访客网络一般会禁止设备间相互访问，会导致无法添加；
2. 无密码WiFi：密码框为空直接Submit即可；
3. 隐藏WiFi：先临时将WiFi设置成可见，配置连接成功后再设置成隐藏即可；

<table style="table-layout: fixed; width: 100%; border-collapse: collapse;" border="1">
  <tr>
    <td style="text-align: center;">
      <img src="/assets/ed43cb786850765932d7bcb6ce1cfd2.jpg" alt="有帮助的截图" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/177d07c95dfc6af7d44488f322c696e.png" alt="有帮助的截图" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/bb731c8c7288d89776963b86065934e.jpg" alt="有帮助的截图" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/2e7b26586724e64d2bac8042152e081.jpg" alt="有帮助的截图" style="width: 100%;" />
    </td>
  </tr>
  <tr>
    <td style="text-align: center;">填入<code>家里WiFi</code>的密码，并提交(SUBMIT)</td>
    <td style="text-align: center;">等待设备连网...(大约30秒)</td>
    <td style="text-align: center;">输入<code>46637726</code>并保存(SAVE Settings)</td>
    <td style="text-align: center;">提示完成，等待界面自动跳回</td>
  </tr>
</table>

# 2. 添加

在 Home Assistant 中，依次进入 设置 → 设备与服务 → 添加集成，搜索「HomeKit」，结果如下图所示：

| [<img src="/assets/20260329212736.jpg" width="600"/>](/assets/20260329212736.jpg)|
| :------------: | 
|          电脑版    |

| [<img src="/assets/cbe4dd57dc752d144ca38bb6f62d8e2f.jpg" width="240"/>](/assets/cbe4dd57dc752d144ca38bb6f62d8e2f.jpg)|
| :------------: | 
|          手机版    |


## 2.1 选择设备

在列表中选择自动发现的 HomeKit 设备，点击进入添加流程。

| [<img src="/assets/20260329212745.jpg" width="600"/>](/assets/20260329212745.jpg)|
| :------------: | 
|          电脑版    |

## 2.2 输入配置代码

输入设备提供的 8 位 HomeKit 配对码：

`4663 7726`

（图待补充）

## 2.3 完成配对

配对成功后，Home Assistant 会自动添加该设备，并生成对应的控制实体，可在「概览」页直接使用。

# 3. 搜索不到设备？

通常是设备未成功恢复出厂所致。请重新执行步骤 1.1，确认指示灯完成熄灭后再重试配对。

| [<img src="/assets/963c520bfe3c1e4d5c4884d1de6600d2.jpg" width="240"/>](/assets/963c520bfe3c1e4d5c4884d1de6600d2.jpg)|
| :------------: | 
|          搜索不到设备？    |

[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html