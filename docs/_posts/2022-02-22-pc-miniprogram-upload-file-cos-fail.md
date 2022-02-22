---
layout: post
title:  "微信小程序电脑版直传COS失败"
date:   2022-02-22 22:55:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

一个在手机端使用的小程序，用户反馈想要在电脑端能使用，改了一个选择视频的API之后，还有一个不兼容-直传COS。直接说结果就是COS的sdk中FileSize不能填写，填写就上传失败报403。不填写就办法显示进度条给用户，我是直接不显示进度条了。

下面来说我经过哪些分析：



[1]: https://coolshell.cn/articles/17998.html
