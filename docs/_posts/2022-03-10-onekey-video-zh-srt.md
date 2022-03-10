---
layout: post
title:  "一键中文字幕"
date:   2022-03-10 21:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

一键中文字幕，是一个一键为视频上字幕的工具，纯手机小程序操作简单方便。

# 使用

1. 短按选相册
2. 长按选择聊天
3. 滑动剪贴板链接
4. 播放完毕后，长按视频保存

| ![有帮助的截图](/assets/onekey_srt.jpg) |
| :----------------------------------------: |
|          *软件架构图*          |

| ![有帮助的截图](/assets/WX20220310-224530.png) |
| :----------------------------------------: |
|          *添加字幕后的效果*          |

# 架构图

| ![有帮助的截图](/assets/onekey_srt_jiagou.jpg) |
| :----------------------------------------: |
|          *软件架构图*          |

# 技术栈

| 视频源 | 语音识别 | 翻译 | 合成字幕 |
| :---- | :---- | :---- | :---- |
| √相册/聊天 | √阿里云 | √谷歌云 | √Amazon MediaConvert  |
| √Twitter | √谷歌云 | - |  ffmpeg |
| YouTube       | Amazon Transcrible | - | - |
| Facebook      | 百度云 | -| - |
| Instagram     | IBM云 | - |  - |
| TikTok        | Azure | - |  - |
| 相册不压缩      | 讯飞 | - |  - |
| 网页       | 腾讯云 | - |  - |
| APP  | DeepSpeech | - |  - |
| -             | 原字幕OCR | - |  - |
