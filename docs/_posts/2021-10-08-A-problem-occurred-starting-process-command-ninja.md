---
layout: post
title:  "failed: Connection closed before receiving a handshake response"
date:   2021-10-08 18:20:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

```
A problem occurred starting process 'command '...bin\ninja.exe'
```
将app/.cxx目录全部删除后会报如下错误：
```
app/.cxx/cmake/debug/armeabi-v7a/android_gradle_build.json (No such file or directory)
```

```
rm -rf ./app/.cxx/
rm ./.idea/
```