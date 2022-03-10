---
layout: post
title:  "一键中文字幕"
date:   2022-03-10 21:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

一键中文字幕，架构图如下

| ![有帮助的截图](/assets/onkey_srt_jiagou.jpg) |
| :----------------------------------------: |
|          *软件架构图*          |

| 视频源 | 语音识别 | 翻译 | 合成字幕 |
| :---- | :---- | :---- | :---- |
| :keycap_ten:相册/聊天 | :keycap_ten:阿里云 | :keycap_ten:谷歌云 | :keycap_ten:Amazon MediaConvert  |
| :nine:Twitter | :keycap_ten:谷歌云 | - |  :parking:ffmpeg |
| :one:YouTube       | :parking:Amazon Transcrible | - | - |
| Facebook      | 百度云 | -| - |
| Instagram     | :no_entry_sign:IBM云 | - |  - |
| TikTok        | :no_entry_sign:Azure | - |  - |
| :pencil2:相册不压缩      | :wheelchair:讯飞 | - |  - |
| :parking:网页       | :parking:腾讯云 | - |  - |
| :parking:APP  | :parking:DeepSpeech | - |  - |
| -             | :pencil2:原字幕OCR | - |  - |
