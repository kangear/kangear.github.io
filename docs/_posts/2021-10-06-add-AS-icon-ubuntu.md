---
layout: post
title:  "Ubuntu 20.04添加Android Studio图标"
date:   2021-10-06 22:56:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

# 前言

Ubuntu上安装`Android Studio`比较简单，下载压缩包解压即可。启动方式是在终端运行`bin/studio.sh`可以验证安装是否成功。

# 桌面图标
安装成功之后就需要添加图标了，和16.06能直接放到桌面不同，20.04必须将图标放到`/usr/share/applications`下，否则不能运行。

```
sudo gedit /usr/share/applications/as.desktop
```
内容：
```
[Desktop Entry]
Name=Android Studio
Exec=/home/tony/Work/02_sw/android-studio-2020.3.1.24-linux/android-studio/bin/studio.sh
Icon=/home/tony/Work/02_sw/android-studio-2020.3.1.24-linux/android-studio/bin/studio.png
Terminal=false
Type=Application
```
保存后即可在搜索栏搜索到应用，如下图所示：

![有帮助的截图](/assets/Screenshot from 2021-10-06 22-50-49.png)
