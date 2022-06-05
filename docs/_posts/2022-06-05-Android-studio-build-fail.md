---
layout: post
title:  "Android Studio编译提示androidx.camera:camera-view:1.0.0-alpha27 失败，mvnrepository相关"
date:   2022-06-05 17:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

比如是提示这个：
```
androidx.camera:camera-view:1.0.0-alpha27 mvnrepository.com
```

怎么弄都不行，其实打开`https://mvnrepository.com/artifact/androidx.camera/camera-view/1.0.0-alpha27`网址，会发现需要“人机验证”。


| ![有帮助的截图](/assets/WX20220605-182840.png) |
| :----------------------------------------: |
|          *人机验证*          |

或者换个节点应该也能解决问题。
