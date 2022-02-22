---
layout: post
title:  "视频字幕（视频翻译）"
date:   2022-02-19 22:55:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 腾讯云音视频字幕平台(排除)
小程序可以叫“视频翻译”或者“双语字幕”，就是把视频上字幕。[腾讯云音视频字幕平台(transfy)][1]支持的功能有：能够覆盖音视频字幕转写翻译、直播字幕、多语言字幕、自动切割时间轴、字幕样式编辑、字幕视频压制等多种场景，轻松搞定字幕制作难题。可以导致内字幕。

但是遇到个API可以创建任务，但是无法下载合成后的视频。咨询的时候官方如此回复：未通过审核，该产品目前正在下线阶段，感谢您的支持，谢谢。

看来已经要下线了，我说怎么有点low呢。

# 阿里云媒体处理(排除)
在任务管理模块中，您可以将视频文件通过单项任务快速生成媒体文件，单项任务包含转码、智能封面、视频审核、视频DNA、智能标签。本文介绍了如何创建提交单项任务，并查看任务提交后的执行状态和详细信息。

# 自己写Python脚本实现(成功)
https://www.assemblyai.com/blog/how-to-add-subtitles-to-your-mux-videos-with-python/

借助[Google翻译][1] + [腾讯云上部署流式转码应用][2] + [burns the subtitles][3]

| ![有帮助的截图](/assets/WX20220219-184516.png) |
| :----------------------------------------: |
|          *原问题*          |

把`subtitles.srt`下载到`/tmp/`目录下，然后执行这个命令

```
ffmpeg -i mymovie.mp4 -vf subtitles=subtitles.srt mysubtitledmovie.mp4
```


参考：
1. https://transfy.cloud.tencent.com/

[1]: https://translate.google.cn/
[2]: https://kangear.github.io/cloud/2021/12/18/tcloud.html
[3]: https://stackoverflow.com/a/13125122/2193455
