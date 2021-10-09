---
layout: post
title:  "Ubuntu遇上U盘"
date:   2021-10-08 18:20:05 +0800
categories: ubuntu
typora-copy-images-to: ../asserts
typora-root-url: ../
---

如果觉得 ubuntu 默认 自动 挂载 u 盘会因为 写入 缓冲 而导致复制文件到 u 盘时 进度条 不准确，或者写完后弹出比较慢，
那可以考虑修改 udisk2 配置让自动挂载时加上 flush 参数。

如果觉得 flush 不够彻底还可以继续加上 sync 参数（注意 sync 会慢不少）

另外，通常 ubuntu 默认的 `udisks2` 配置自动挂载就已经给 vfat 和 `exfat` 加上 `flush` 参数了，
所以你直接把 u盘格式（文件系统）改为 fat32 或 exfat 就能让复制文件进度条更准，弹出更快。
即通常只是在 u盘上用 `ntfs` 或 `ext4` 时会感觉到文件复制进度条和弹出时间问题。

下方列出的配置文件里可以不写 `vfat` 和 `exfat` 部分（如果你的系统里原本就有 `flush` 参数）。

如果不在乎副作用，
可以新建文件 `/etc/udisks2/mount_options.conf`
写入
```
[defaults]
defaults=ro,flush
allow=exec,noexec,nodev,nosuid,atime,noatime,nodiratime,ro,rw,sync,dirsync,noload,flush
```
如果稍微在乎下其他文件系统的副作用，可以只修改 vfat、exfat 和 ntfs，即改为写入
```
[defaults]
defaults=ro
allow=exec,noexec,nodev,nosuid,atime,noatime,nodiratime,ro,rw,sync,dirsync,noload,flush
vfat_defaults=uid=$UID,gid=$GID,shortname=mixed,utf8=1,showexec,flush
exfat_defaults=uid=$UID,gid=$GID,iocharset=utf8,errors=remount-ro,flush
ntfs_defaults=uid=$UID,gid=$GID,windows_names,flush
```
如果觉得 flush 不够彻底，可以考虑加上 sync，但注意会让速度慢不少
```
[defaults]
defaults=ro
allow=exec,noexec,nodev,nosuid,atime,noatime,nodiratime,ro,rw,sync,dirsync,noload,flush
vfat_defaults=uid=$UID,gid=$GID,shortname=mixed,utf8=1,showexec,flush,sync
exfat_defaults=uid=$UID,gid=$GID,iocharset=utf8,errors=remount-ro,flush,sync
ntfs_defaults=uid=$UID,gid=$GID,windows_names,flush,sync
```
除了修改 udisks2 配置外，还可以用更高一级的 udev 规则，
比如新建文件 /etc/udev/rules.d/10-usb-disk.rules
写入
```
ACTION=="add", BUS=="usb", ENV{ID_FS_TYPE}=="vfat|exfat|ntfs", ENV{mount_options}="rw,flush,sync"
```
执行重载命令
```
sudo udevadm control --reload-rules 
```
再插入U盘不会有问题了。