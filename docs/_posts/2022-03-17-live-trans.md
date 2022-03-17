---
layout: post
title:  "直播添加字幕和翻译"
date:   2022-03-17 21:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

王局亲提到需求，头发掉光也要努力做出来。以下是目前了解到的信息，实时更新。在语音识别领域的术语叫`实时语音识别`，表现最出色的依然是Google。居然在Chrome中免费支持了，你看到屏幕上的任何英文视频均自动进行字幕显示功能。目前是收集资料阶段，收集好就知道下一步怎么做了。

# 先说结论
如果只看英文字幕（英文阅读能力强，听力弱的），可以使用`Chrome Live Caption`功能，非常好用。就像和`Siri`对话练习英文一样，看似扯蛋，其实比较实用。其实还可以实现无声看视频，因为调静音也可以自动出字幕。如果需要实时中文字幕，则需要我再进一步调研和开发。

# 现状
YouTube少量在自动识别字幕，但是不支持翻译。Twitter更不支持字幕。

| ![有帮助的截图](/assets/IMAGE_03172246.jpg) |
| :----------------------------------------: |
|          Chrome Live Caption效果2         |

# 云厂家对比

| 视频源 | 支持格式 | - | - |
| :---- | :---- | :---- | :---- |
| [阿里云][4]                | PCM（无压缩的PCM或WAV文件）、16 bit采样位数、单声道（mono）        | -     | -  |
| [百度云][3]                | 目前只支持pcm格式的原始音频数据， 16000采样率， 单声道，16bits，小端序 | -      |  - |
| [讯飞][1]([实时语音转写][2]) | 采样率为16K，采样深度为16bit的pcm_s16le音频  | -   | - |
| [Chrome(Live Caption)][5] | Chrome自带功能，本为听力障碍者使用Twitter/Youtube测试均可           |            -     | - |

# Chrome Live Caption（重点）

## 打开方法

| ![有帮助的截图](/assets/WX20220317-233315.png) |
| :----------------------------------------: |
|          打开方法        |

## 效果
| ![有帮助的截图](/assets/WX20220317-230616.png) |
| :----------------------------------------: |
|          Chrome Live Caption效果1        |

| ![有帮助的截图](/assets/WX20220317-231102.png) |
| :----------------------------------------: |
|          Chrome Live Caption效果2         |

| ![有帮助的截图](/assets/WX20220317-231738.png) |
| :----------------------------------------: |
|          Chrome Live Caption效果 直播        |


未整理资料

https://aws.amazon.com/cn/about-aws/whats-new/2021/05/amazon-transcribe-improves-live-subtitling-partial-results-stabilization/  
https://github.com/luvletter2333/Live-SubTitle  
https://support.google.com/youtube/answer/3068031?hl=zh-Hans  


[1]: https://www.xfyun.cn/services/rtasr
[2]: https://www.xfyun.cn/doc/asr/rtasr/API.html
[3]: https://cloud.baidu.com/product/speech/realtime_asr
[4]: https://help.aliyun.com/document_detail/84428.html
[5]: https://support.google.com/chrome/answer/10538231?hl=en
