---
layout: post
title:  "在Ubuntu 16.04上编译Android 12(LineageOS 19.0)"
date:   2021-10-17 23:35:05 +0800
categories: android
typora-copy-images-to: ../asserts
typora-root-url: ../
---

# How to Build LineageOS 19.0 ROM on Ubuntu 16.04
# 在Ubuntu 16.04上编译LineageOS 19.0 | Android 12

https://wiki.lineageos.org/devices/walleye/build

Pixel 2: walleye


# 前言

`LineageOS 19.0`代码发布还没有几天，编译可以不会太顺利。以下的步骤是从`编译早期版本`时总结下来了，还没有确认到底。

目前遇到的问题有：
1. 代码能下载完，但是缺少`vendor`目录，这也是奇怪
2. 没有了`breakfast`命令，也可能还没有支持，暂时使用aosp的命令在编译（https://source.android.com/setup/build/building）
我已经在群里问了，有更新的话，我会更新到此文章上。


# 初始化代码仓库
```shell
repo init --repo-branch v2.0 -u https://github.com/LineageOS/android.git -b lineage-19.0 --depth 1
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
