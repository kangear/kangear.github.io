---
layout: post
title:  "米家Beta调试时总出现 设备已离线 弹窗"
date:   2024-10-02 00:20:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

按照[米家APP 扩展程序开发][1]安装好了开发环境，也可以运行Demo，但是出现如下弹窗比较干扰

| ![有帮助的截图](/assets/63cc055b2cee03ee8e4b293bb807d45.jpg) | ![有帮助的截图](/assets/5cd62352a99c4a4acc1edcb798f3179.jpg) |
| :----------------------------------------: | :----------------------------------------: |
|          *命令行*          |         *设备已离线弹窗*          |

# 安装过程

补充一些安装过程，比如特别的设置了代理，才能准确安装

## 淘宝node镜像已经禁用改为官方

```diff
diff --git a/bin/install_mihome_dev.bat b/bin/install_mihome_dev.bat
index c2466c5a..5fe69fef 100644
--- a/bin/install_mihome_dev.bat
+++ b/bin/install_mihome_dev.bat
@@ -86,7 +86,7 @@ goto listMenu
     echo 2 <B0><B2>װ watchman <BF><AA><B7><A2><BB><B7><BE><B3>
     echo 3 <D0>޸<B4> node_modules <D7><CA>Դ
     SET /P FUNC=<C7><EB>ѡ<D4><F1><A3><BA>
-    IF "%FUNC%" == "1" CALL :installBinary https://npm.taobao.org/mirrors/node/v12.16.1/node-v12.16.1-win-x64.zip  node-v12.16.1-win-x64   "node -v"
+    IF "%FUNC%" == "1" CALL :installBinary https://nodejs.org/dist/v12.16.1/node-v12.16.1-win-x64.zip  node-v12.16.1-win-x64   "node -v"^M
     IF "%FUNC%" == "2" CALL :installBinary http://cdn.cnbj0.fds.api.mi-img.com/miio.files/commonfile_zip_895012f81cb3668260b0e8bec291b5f9.zip watchman-v2020.08.17.00-windows/bin "watchman -v"
     IF "%FUNC%" == "3" CALL :fixEnviroument
```

## 设置代理

```
npm config set http-proxy http://127.0.0.1:7890
npm config set https-proxy http://127.0.0.1:7890
```

[1]: https://iot.mi.com/new/doc/accesses/direct-access/extension-development/quick-start/the-first-extension
