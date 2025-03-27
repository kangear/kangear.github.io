---
layout: post
title:  "HomeKit配件使用说明"
date:   2024-11-15 12:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

本文同样适应于无极调光灯、彩灯、USB通断器、温度计、手指机器人、门铃等。

# 开始之前

1. 请首先确保iPhone连接2.4G WiFi，而非5G WiFi
2. 将配件上电，观察指示灯处于`每秒快闪两次`状态

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/9debfe9a1066131be503656b2fc42076.mp4#t=0.001" type="video/mp4">
</video>

# 配网流程

| ![有帮助的截图](/assets/0450cf71df2b134490c55be082146aa.jpg) | ![有帮助的截图](/assets/2af4ce7a5c2f9d8d545d5edaa7639bf.jpg) | ![有帮助的截图](/assets/4d8065c835c32a00ea48c0c7abe5201.jpg) | ![有帮助的截图](/assets/2c75de776b1064cf6004fa926e3a70e.jpg) |
| :------------: | :------------: | :------------: | :------------: |
|  iPhone中会多一个WiFi热点`HomeSpan-Setup`  |  输入密码`homespan`连接    |  按`下箭头`打开WiFi弹窗*    |     *为设备选择`家里WiFi`，这里以`QWRT-2.4G`为例*          |

| ![有帮助的截图](/assets/ed43cb786850765932d7bcb6ce1cfd2.jpg) | ![有帮助的截图](/assets/177d07c95dfc6af7d44488f322c696e.png) | ![有帮助的截图](/assets/4d8a5222ecda1cb52b8bb51f61bffaa.jpg) |![有帮助的截图](/assets/2e7b26586724e64d2bac8042152e081.jpg) |
| :------------: | :------------: | :------------: | :------------: |
|  填入`家里WiFi`的密码，并提交(SUBMIT)   |  等待设备连网...(大约30秒)   |    *保持为空，直接保存(SAVE Settings)*    |      *提示完成*   | 

说明：    
1. 此时指示灯会`每秒慢闪两次`代表`连网成功，等添加到家庭`状态
2. WiFi热点`HomeSpan-Setup`会消失

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/f5b0fb973aeea8e454ecad0cc1c70c8e.mp4#t=0.001" type="video/mp4">
</video>

# Home App添加

| ![有帮助的截图](/assets/fb41812deab0d36c92f432cedeeeb32.jpg) |![有帮助的截图](/assets/13bde97741334546e64593ec61ff82a.jpg) | ![有帮助的截图](/assets/b49043a0190c557b5c6236fec8d1c0a.jpg) | ![有帮助的截图](/assets/7cae940a751d817b6ab05cad42b8b72.jpg) | ![有帮助的截图](/assets/35140c818ffed06026eab2d5f2887ca.jpg) | 
| :------------: | :------------: | :------------: | :------------: | :------------: |
|          *打开家庭App*    |      *点击右上角+号*    |  *添加或扫描配件*    |     *选择 更多选项*          |     *选择Light(请以实际为准)*          |


| ![有帮助的截图](/assets/7d88f9fc7d5150eaf866990a28d7020.jpg) | ![有帮助的截图](/assets/146d812327b60b10c5e6fb8169558b0.jpg) | ![有帮助的截图](/assets/42ee7ba479d76aa52de513c84859537.jpg) | ![有帮助的截图](/assets/9a195f3b1310cee2b78d76a62399f8c.jpg) | ![有帮助的截图](/assets/cc975a7a83ba6b618c3d18610ac9d9b.jpg) |
| :------------: | :------------: | :------------: | :------------: | :------------: |
|          *选择仍然添加*    |      *输入设置代码`4663 7726`并继续*    |  *选择位置*    |     *选择 完成*          |     *完成*          |

说明：    
1. 此时指示灯会`常亮`代表`已加到家庭`状态
2. 如出现弹窗`无法添加配件`内容为`配件不可连接`，重开一下手机WiFi再次添加即可。

# 使用控制

1. 可以通过`家庭App`控制   
触摸黄色图标直接开关；

2. 可以通过`Siri`控制   
`Siri 开灯`
`Siri 关灯`

3. 通过`控制中心`控制

# 恢复出厂

设备上的按钮`长按10秒钟`指示灯由闪烁到熄灭，即可恢复出厂。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/b98a5f7368f729e9e6152d88bc56bb44.mp4#t=0.001" type="video/mp4">
</video>

### 常见问题
[HomeKit USB伴侣配网添加不成功？][1]

[1]: /cloud/2025/03/06/HomeKit-Pair-Fail.html