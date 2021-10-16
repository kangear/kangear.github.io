---
layout: post
title:  "在Ubuntu 16.04上编译LineageOS 17.1(10.0)系统"
date:   2021-10-14 23:32:05 +0800
categories: android
typora-copy-images-to: ../asserts
typora-root-url: ../
---

# How to Build LineageOS 17.1 ROM on Ubuntu 16.04
# 在Ubuntu 16.04上编译LineageOS 17.1(10.0)系统

https://wiki.lineageos.org/devices/walleye/build

Pixel 2: walleye

# 初始化代码仓库
```shell
repo init --repo-branch v2.0 -u https://github.com/LineageOS/android.git -b lineage-17.1 --depth 1
```

# 配置私有驱动仓库
```shell
mkdir -p .repo/local_manifests/
gedit .repo/local_manifests/roomservice.xml
```

内容如下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="TheMuppets/proprietary_vendor_google" path="vendor/google" remote="github"/>
</manifest>
```

# 下载代码
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
