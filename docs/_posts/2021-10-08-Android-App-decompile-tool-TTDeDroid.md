---
layout: post
title:  "Android App反编译工具-TTDeDroid和Android Killer"
date:   2021-10-08 18:11:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

反编译Android App我一般使用`TTDeDroid`和`Android Killer`。前者可以一键反编译成`Java`代码方便查看代码。后者集成了`回编译`工具，比较方便回编译。两者结合使用极为方便。

# TTDeDroid
[下载地址](https://github.com/tp7309/TTDeDroid)，几乎是一键反编译。如果对大于100M的App可能需要修改一个虚拟机内存大小。如下：
```diff
diff --git a/libs/jadx/bin/jadx-gui b/libs/jadx/bin/jadx-gui
index 131a97e..c86b948 100755
--- a/libs/jadx/bin/jadx-gui
+++ b/libs/jadx/bin/jadx-gui
@@ -28,7 +28,7 @@ APP_NAME="jadx-gui"
 APP_BASE_NAME=`basename "$0"`
 
 # Add default JVM options here. You can also use JAVA_OPTS and JADX_GUI_OPTS to pass JVM options to this script.
-DEFAULT_JVM_OPTS='"-Xms128M" "-Xmx4g" "-Dawt.useSystemAAFontSettings=lcd" "-Dswing.aatext=true" "-XX:+UseG1GC"'
+DEFAULT_JVM_OPTS='"-Xms128M" "-Xmx8g" "-Dawt.useSystemAAFontSettings=lcd" "-Dswing.aatext=true" "-XX:+UseG1GC"'
 
 # Use the maximum available, or set MAX_FD != -1 to use that value.
 MAX_FD="maximum"
```

# Android Killer
待更新