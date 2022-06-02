---
layout: post
title:  "Mac安装MySql"
date:   2022-06-02 17:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---
```
brew instal mysql
```
后报错：
`ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock'`


执行以下命令解决：（果真又和/usr/local有关）
```
sudo chown -R _mysql:mysql /usr/local/var/mysql

sudo mysql.server start
```
来自：https://stackoverflow.com/a/40736952/2193455


接着看：
https://flaviocopes.com/mysql-how-to-install/
