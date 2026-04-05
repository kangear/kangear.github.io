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