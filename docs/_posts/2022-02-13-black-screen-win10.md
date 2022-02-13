---
layout: post
title:  "Win10安装软件后启动不起来（黑屏）"
date:   2022-02-13 13:46:05 +0800
categories: blog
typora-copy-images-to: ../assets
typora-root-url: ../
---

安装了一个“Usb over Network”的软件`usb-for-remote-desktop-server-64bit.msi`，Win10就启动不起来了，表现为黑屏。采用`还原`总不成功。下面采用了`安全模式`卸载出问题的软件解决了问题。

# 方案1：系统还原（失败）

| ![有帮助的截图](/assets/WechatIMG146.jpeg) |
| :----------------------------------------: |
|          *原问题*          |

失败了。

# 方案2：安全模式修复
怎么进不讲了，网上很容易查到。

## 卸载时出错
由于安装的是msi文件，所以需要借助`Windows Installer`卸载，我同步卸载了

| ![有帮助的截图](/assets/WechatIMG147.jpeg) |
| :----------------------------------------: |
|          *原问题*          |

### Windows Installer图形化启动时报错

| ![有帮助的截图](/assets/WechatIMG148.jpeg) |
| :----------------------------------------: |
|          *原问题*          |

### Windows Installer命令行启动
打开命令行 执行
```shell
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\SafeBoot\Minimal\MSIServer" /VE /T REG_SZ /F /D "Service"
（各个选项如/ve /t /f /d 等一般小写）
```
创建安装服务并启动
```shell
net start msiserver 
```
可以看到终端打印了启动成功。

来自：[https://blog.51cto.com/sddai/3078363][1]

## 再次卸载
卸载成功，重启后正常了。

# 总结
Win10已经具有`系统还原`和`安全模式`比较好用，不用借助PE系统也能做一些简单的修复工作。装上就黑屏有点奇怪，看恢复显示很有可能是装了两个？就没有做进一步测试了。问题已经解决了。

[1]: https://blog.51cto.com/sddai/3078363
