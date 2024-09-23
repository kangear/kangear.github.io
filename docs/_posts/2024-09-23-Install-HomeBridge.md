---
layout: post
title:  "HomeBridge初体验"
date:   2024-09-23 11:30:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

前几天，在读一篇HomeKit好文时文中提到了`HomeBridge`，今天终于有机会体验一下，好文是《[HomeKit 从零完全入门指南（一）：认识 HomeKit][1]》。我的知识背景是前年体验过Aqara的M1S网关，使用起来非常方便；还有最近刚用起来涂鸦的HomeKit模组，成功配置到了Home App中使用，但只是测试，如果想要商用得自行申请MFi。一想到需要申请MFi采能这样接入就比较麻爪，看似一个好功能确差点意思，仿佛只有财大气粗的大厂可以方便的集成。

看到HomeBridge也能生产`8位数字代码`，能被Home App添加并识别，只是会显示“未认证”而已，我突然就来了兴趣，因为这从原理上消除了对HomeKit WiFi模组的担心，如果HomeKit WiFi模组比如涂鸦、ESP32也可以采用HomeBridge的方式，只是生产一个未认证的设备，那将是一个广阔的天地，将有大量的低价的Home配件被制造出来。

下面体验一下HomeBrigde，比较百闻不如一见。

# 安装过程

| ![有帮助的截图](/assets/微信截图_20240923103805.png) |
| :----------------------------------------: |
|          *1*          |

| ![有帮助的截图](/assets/微信截图_20240923103836.png) |
| :----------------------------------------: |
|          *2*          |

| ![有帮助的截图](/assets/微信截图_20240923103850.png) |
| :----------------------------------------: |
|          *3*          |

| ![有帮助的截图](/assets/微信截图_20240923103914.png) |
| :----------------------------------------: |
|          *3*          |


| ![有帮助的截图](/assets/微信截图_20240923105508.png) |
| :----------------------------------------: |
|          *3*          |

# Home App识别

| ![有帮助的截图](/assets/4e805ba681af95243f2f42236a6b646.jpg) | ![有帮助的截图](/assets/f64c430c642e22ae9757c6a409cdf07.jpg) | ![有帮助的截图](/assets/a2cc7b74fdfb12acfa19d03b98583b1.jpg) | ![有帮助的截图](/assets/630e190620e0c19074bc2bf73311b42.jpg) |
| :----------------------------------------: | :----------------------------------------: | :----------------------------------------: | :----------------------------------------: |
|          *3*          |         *3*          |         *3*          |         *3*          |

# 安装一个虚拟灯插件

| ![有帮助的截图](/assets/微信截图_20240923105710.png) |
| :----------------------------------------: |
|          *3*          |

| ![有帮助的截图](/assets/微信截图_20240923105726.png) |
| :----------------------------------------: |
|          *3*          |

| ![有帮助的截图](/assets/微信截图_20240923115418.png) |
| :----------------------------------------: |
|          *3*          |

# Home App 联动

| ![有帮助的截图](/assets/0c659350386c85159c88928b335c70a.jpg) | ![有帮助的截图](/assets/9f6aa4d43cebdbdcc18abb7b971b8de.jpg) |
| :----------------------------------------: | :----------------------------------------: |
|          *3*          |         *3*          |

# 小结

我体验的目的也十分明确，只是为了弄明白设备配网时`8位数字代码`从哪里来，是技术上的还是商务上的，如果已经证明主要是技术上的，如果商务上没有做，只是会出现未认证，使用起来倒无关紧要。这个HomeBridge如果要引入小米设备的控制，比如小米扫地机器人，还需要像黑客一样填写其IP地址型号等信息[这里][2]，这个一般消费者搞不定，所以`销售HomeBridge网关`并非我这次体验的重点方向。

[1]: https://sspai.com/post/67784
[2]: https://github.com/homebridge-xiaomi-roborock-vacuum/homebridge-xiaomi-roborock-vacuum
