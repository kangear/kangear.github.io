---
layout: post
title:  "Android Studio遇到ValidatorException: PKIX path building failed"
date:   2024-10-14 00:20:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

Android Studio新建了一个HelloWorld居然都报错，这是一个老版本3.6，其实能猜测出大概问题，网站的增收更换了，就如同清朝胡同停不下21世纪的汽车，除非一个一个问题解决才可以，Android Studio 3.6是胡同，Gradle版本和依赖就是21世纪的汽车。

最后使用toolbox下载了一个新版本，但也相对旧的版本`Android Studio Electric Eel`，该版本还支持使用Java作为开发语言，不像最新的2024已经不支持了，新的Kotlin语言始终没有学习，所以一直躲避着使用这个语言。

```
Android Studio Electric Eel | 2022.1.1 Patch 2
Build #AI-221.6008.13.2211.9619390, built on February 17, 2023
Runtime version: 11.0.15+0-b2043.56-9505619 amd64
VM: OpenJDK 64-Bit Server VM by JetBrains s.r.o.
Windows 10 10.0
GC: G1 Young Generation, G1 Old Generation
Memory: 2030M
Cores: 8
Registry:
    external.system.auto.import.disabled=true
    ide.text.editor.with.preview.show.floating.toolbar=false
```

