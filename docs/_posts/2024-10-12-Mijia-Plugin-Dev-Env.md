---
layout: post
title:  "米家插件开发环境搭建"
date:   2024-10-12 15:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 效果演示

按照我的思路，一般会先进行最终效果演示，这样方便读者能快速有一个初步印象。

| ![有帮助的截图](/assets/63eb7bb4f859ab4dfa6e097fb054849.jpg) |
| :----------------------------------------: |
|          *效果演示*          |

# 和微信小程序对比

| 类别 | 微信小程序 | 米家插件 | Android | 备注 |
| ---: | :----: | :----: | :----: | :----: |
|  设备  | 模拟器/真机 | 真机 | 模拟器/真机 |
|  App  | 微信App | 米家Beta App  | Android系统  |  |
|  开发环境  | 微信开发者工具 | vscode + cmd终端  | Android Studio  |  |
|  项目关联  | AppId | 包名  | ApplicationId  |  |
|  连接  | 互联网 | WiFi  | USB/WiFi  |  |
|  账户  | 需成为开发者 | 需成为开发者  | -  |  |
|  调试状态   | 默认 | 扫码  | 打开开发者选项  |  |
|  入口图标  | 自动生成 | [小米AIoT平台高仿真系统][1] 上添加设备 | -   | - |
|  进入界面  | 自动 | 点击设备 | 自动 | - |
|  所见即所得  | 是 | 是 | 是  | - |

# 环境搭建

首先需要吐槽的是，互联网仿佛是一个巨大的垃圾桶，我仿佛是那个拾荒者，米家这种平台向互联网上丢了很多文档，而我的这个拾荒者需要翻来覆去的寻找我真正需要的内容。就好比想知道生火的方法，会搜索出钻木取火的相关介绍，好容易找到适合自己的打火机方式，有些步骤的理解却需要从钻木取火流程中获取。

最新的入口：
https://iot.mi.com/v2/new/doc/plugin/quickstart/quick-start

过时的入口：
https://github.com/MiEcosystem/miot-plugin-sdk/tree/master
https://iot.mi.com/new/doc/accesses/direct-access/extension-development/quick-start/the-first-extension

按照正确入口安装后环境后，想运行一个Demo，一般会按照`不修改一行代码`的思路，比如：
```
npm start com.xiaomi.demo
```
实际会遇到[米家Beta调试时总出现 设备已离线 弹窗][2]，调试的时候需要保证文件夹名字就是设备的model名字才会关联起来：

| ![有帮助的截图](/assets/c50a008e5e158cc64461e171743f966.jpg) | ![有帮助的截图](/assets/7ffbd8b498a137e163b743d5a728cdc.jpg) |
| :----------------------------------------: | :----------------------------------------: |
|          *点击设备后弹窗*          |         *HelloWorld*          |

[1]: https://vd.iot.mi.com/home
[2]: https://kangear.github.io/cloud/2024/10/01/Mijia-Beta-Device-offline-Dialog.html
