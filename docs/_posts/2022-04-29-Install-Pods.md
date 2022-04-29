---
layout: post
title:  "安装CocoaPods"
date:   2022-04-29 17:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 安装
来自：https://www.jianshu.com/p/fb7f533c39fc
```shell
gem sources --remove https://rubygems.org/
gem sources -a https://gems.ruby-china.com/
sudo gem install cocoapods
pod setup
```

# 配置
来自：https://www.jianshu.com/p/4a118f93e6ed
```shell
cd ~/.cocoapods/repos
pod repo remove master
git clone https://mirrors.tuna.tsinghua.edu.cn/git/CocoaPods/Specs.git master
# 再改回来
cd master
git remote set-url origin https://github.com/CocoaPods/Specs.git
```
