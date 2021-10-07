---
layout: post
title:  "在Ubuntu 16.04上编译LineageOS 16.0(9.0)系统"
date:   2021-10-07 17:11:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

# How to Build LineageOS 16.04 ROM on Ubuntu 16.04
# 在Ubuntu 16.04上编译LineageOS 16.0(9.0)系统

https://wiki.lineageos.org/devices/walleye/build

Pixel 2: walleye


# 初始化
```shell
repo init -u https://github.com/LineageOS/android.git -b lineage-16.0 --depth 1
```

# 下载代码
## 同步代码
```
repo sync -j32
```

## 同步代码脚本
```shell
#!/bin/bash

repo sync -j32
while [ $? -ne 0 ]
do
    repo sync -j32
done
```

# 编译
```
export PHONE_NAME=walleye
source build/envsetup.sh && breakfast ${PHONE_NAME} && brunch ${PHONE_NAME}
```
# FASTBOOT烧写（刷机）
主要是`system.img userdata.img vendor.img boot.img`
```
fastboot flashall -w
```

# 私有驱动
## 方案A
// .repo/local_manifests/roomservice.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="TheMuppets/proprietary_vendor_google" path="vendor/google" remote="github"/>
</manifest>
```
## 方案B
```
./extract-files.sh
```

# OTA固件的编译和刷机
```
adb reboot recovery
adb sideload $OUT/lineage-16.0-xxxxxx-UNOFFICIAL-walleye.zip
```

# 完整固件编译和刷机
## 首先要有证书
略
## 打包成完整固件 
```
brunch ${PHONE_NAME} user && mka target-files-package otatools && ./build/tools/releasetools/sign_target_files_apks -o -d ${CERTS_PATH} $OUT/obj/PACKAGING/target_files_intermediates/*-target_files-*.zip signed-target_files.zip && ./build/tools/releasetools/img_from_target_files signed-target_files.zip signed-img.zip
```
## 刷机
```
fastboot update xxxx.img -w
```
