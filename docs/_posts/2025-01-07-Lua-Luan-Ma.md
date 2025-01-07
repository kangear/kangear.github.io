---
layout: post
title:  "Lua Debug时中文显示为乱码"
date:   2025-01-07 15:00:00 +0800
categories: lua
typora-copy-images-to: ../assets
typora-root-url: ../
---

# Lua Debug调试默认中文日志会显示乱码

| ![有帮助的截图](/assets/微信截图_20250107151510.png) |
| :------------: |
|          *乱码*    | 

# 修改Lua Debug扩展所使用Console

| ![有帮助的截图](/assets/e4ad9e9e427ed055b5e2d9017ed9015.png) |
| :------------: |
|          *由internalTerminal改为internalConsole*    | 

# 中文顺利显示出来

| ![有帮助的截图](/assets/微信截图_20250107151631.png) |
| :------------: |
|          *正常显示中文*    | 

