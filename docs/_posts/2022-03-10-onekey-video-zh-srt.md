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
| √相册/聊天     | √[]阿里云][8]        | √[谷歌翻译][9]     | √Amazon MediaConvert  |
| √Twitter      | √[谷歌云][7]         | [阿里翻译][5]      |  √內嵌字幕 |
| YouTube       | Amazon Transcrible  | [阿里图片翻译][6]   | CC字幕 |
| Facebook      | 百度云               |            -     | ffmpeg |
| Instagram     | IBM云 | - |  - |
| TikTok        | Azure | - |  - |
| 相册不压缩      | 讯飞 | - |  - |
| 网页           | 腾讯云 | - |  - |
| APP           | DeepSpeech | - |  - |
| -             | 有道云 | - |  - |
| -             | [Azure语音翻译][4] | - |  - |
| -             | 原字幕OCR | - |  - |
| -             | [GCP Video Intelligence][1] | - |  - |
| -             | [video-subtitle-extractor][2] | - |  - |
| -             | [colab][3] | - |  - |

[1]: https://cloud.google.com/video-intelligence/docs/feature-text-detection
[2]: https://github.com/YaoFANGUK/video-subtitle-extractor
[3]: https://colab.research.google.com/
[4]: https://azure.microsoft.com/zh-cn/services/cognitive-services/speech-translation/
[5]: https://www.aliyun.com/product/ai/domain_alimt?spm=5176.22414175.J_8058803260.32.6e2e412e7jD7mq
[6]: https://www.aliyun.com/product/ai/alimt/certifictetranslation?spm=5176.22414175.J_8058803260.33.6e2e412e7jD7mq
[7]: https://cloud.google.com/speech-to-text
[8]: https://ai.aliyun.com/nls
[9]: https://cloud.google.com/translate
