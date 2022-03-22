---
layout: post
title:  "直播添加字幕和翻译"
date:   2022-03-17 21:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

如果只看英文字幕（英文阅读能力强，听力弱的），可以使用`Chrome Live Caption`功能，非常好用。就像和`Siri`对话练习英文一样，看似扯蛋，其实比较实用。其实还可以实现无声看视频，因为调静音也可以自动出字幕。如果需要实时中文字幕，则需要我再进一步调研和开发。

# Chrome自带字幕功能Live Caption（重点）

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

## 打开方法

| ![有帮助的截图](/assets/WX20220317-233315.png) |
| :----------------------------------------: |
|          打开方法        |


# 现状（书归正传）

王局亲提到需求，头发掉光也要努力做出来。以下是目前了解到的信息，实时更新。在语音识别领域的术语叫`实时语音识别`，表现最出色的依然是Google。居然在Chrome中免费支持了，你看到屏幕上的任何英文视频均自动进行字幕显示功能。目前是收集资料阶段，收集好就知道下一步怎么做了。

回归到技术正题，YouTube少量在自动识别字幕，但是不支持翻译。Twitter更不支持字幕。

| ![有帮助的截图](/assets/IMAGE_03172246.jpg) |
| :----------------------------------------: |
|          YouTube直播自动字幕        |

# 云厂家对比

| 视频源 | 支持格式 | - | - |
| :---- | :---- | :---- | :---- |
| [阿里云][4]                | PCM（无压缩的PCM或WAV文件）、16 bit采样位数、单声道（mono）        | -     | -  |
| [百度云][3]                | 目前只支持pcm格式的原始音频数据， 16000采样率， 单声道，16bits，小端序 | -      |  - |
| [讯飞][1]([实时语音转写][2]) | 采样率为16K，采样深度为16bit的pcm_s16le音频  | -   | - |
| [Chrome(Live Caption)][5] | Chrome自带功能，本为听力障碍者使用Twitter/Youtube测试均可           |            -     | - |
| [安卓自带Live Transcribe][6] | Chrome自带功能，本为听力障碍者使用Twitter/Youtube测试均可           |            -     | - |

# 推特Live
https://twitter.com/i/broadcasts/1MnxnkaVLyOKO

https://twitter.com/i/events/1504148547049963526

| ![有帮助的截图](/assets/WX20220322-230338.png) |
| :----------------------------------------: |
|          -        |

又叫`events`又叫`broadcasts`还没有搞清楚实现逻辑，但是能看到支持CC，应该是Twitter自己实现的。

```json
{"broadcasts":{"1MnxnkaVLyOKO":{"id":"1MnxnkaVLyOKO","broadcast_id":"1MnxnkaVLyOKO","media_key":"28_1506239529874706436","media_id":"1506239529874706436","created_at_ms":"1647950463137","updated_at_ms":"1647962052452","language":"en","image_url":"https://prod-fastly-us-east-1.video.pscp.tv/Transcoding/v1/live_thumbnail/us-east-1/eyJkIjowfQ/5nGWql69wDF2KNG5Qo5bNSSbPJsLdLLBB-VswKnzatm069gn2GIMJtjICrb2F6v3xgCZPfONLQrzRcLuOwxYTg/latest.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCIsInZlcnNpb24iOiIyIn0.eyJBbGxvd2VkUHJvdG9jb2xzIjpbInRodW1iIl0sIkJyb2FkY2FzdElkIjoiMU1ueG5rYVZMeU9LTyIsIkdyYW50VHlwZSI6InJlYWQiLCJHcmFudGVkQXQiOjE2NDc5NjIwNjEsIkdyYW50ZWRUbyI6InR3LTIyOTQ5NDg3NyIsIlN0cmVhbU5hbWUiOiI1bkdXcWw2OXdERjJLTkc1UW81Yk5TU2JQSnNMZExMQkItVnN3S256YXRtMDY5Z24yR0lNSnRqSUNyYjJGNnYzeGdDWlBmT05MUXJ6UmNMdU93eFlUZyIsImV4cCI6MTY0ODEzNDg2MX0.2U2s97fBpLZusxxae0Gwx7PI78YiVv1vw9UL1F6GfE8&service=proxsee&digest=05c5x4JJJwi6hlvl5V7N-wqcf3nJhfAtkvDIdVVH30o&ts=823981030","image_url_small":"https://prod-fastly-us-east-1.video.pscp.tv/Transcoding/v1/live_thumbnail/us-east-1/eyJkIjoxMjh9/5nGWql69wDF2KNG5Qo5bNSSbPJsLdLLBB-VswKnzatm069gn2GIMJtjICrb2F6v3xgCZPfONLQrzRcLuOwxYTg/latest.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCIsInZlcnNpb24iOiIyIn0.eyJBbGxvd2VkUHJvdG9jb2xzIjpbInRodW1iIl0sIkJyb2FkY2FzdElkIjoiMU1ueG5rYVZMeU9LTyIsIkdyYW50VHlwZSI6InJlYWQiLCJHcmFudGVkQXQiOjE2NDc5NjIwNjEsIkdyYW50ZWRUbyI6InR3LTIyOTQ5NDg3NyIsIlN0cmVhbU5hbWUiOiI1bkdXcWw2OXdERjJLTkc1UW81Yk5TU2JQSnNMZExMQkItVnN3S256YXRtMDY5Z24yR0lNSnRqSUNyYjJGNnYzeGdDWlBmT05MUXJ6UmNMdU93eFlUZyIsImV4cCI6MTY0ODEzNDg2MX0.2U2s97fBpLZusxxae0Gwx7PI78YiVv1vw9UL1F6GfE8&service=proxsee&digest=05c5x4JJJwi6hlvl5V7N-wqcf3nJhfAtkvDIdVVH30o&ts=823981030","image_url_medium":"https://prod-fastly-us-east-1.video.pscp.tv/Transcoding/v1/live_thumbnail/us-east-1/eyJkIjozNjB9/5nGWql69wDF2KNG5Qo5bNSSbPJsLdLLBB-VswKnzatm069gn2GIMJtjICrb2F6v3xgCZPfONLQrzRcLuOwxYTg/latest.jpg?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCIsInZlcnNpb24iOiIyIn0.eyJBbGxvd2VkUHJvdG9jb2xzIjpbInRodW1iIl0sIkJyb2FkY2FzdElkIjoiMU1ueG5rYVZMeU9LTyIsIkdyYW50VHlwZSI6InJlYWQiLCJHcmFudGVkQXQiOjE2NDc5NjIwNjEsIkdyYW50ZWRUbyI6InR3LTIyOTQ5NDg3NyIsIlN0cmVhbU5hbWUiOiI1bkdXcWw2OXdERjJLTkc1UW81Yk5TU2JQSnNMZExMQkItVnN3S256YXRtMDY5Z24yR0lNSnRqSUNyYjJGNnYzeGdDWlBmT05MUXJ6UmNMdU93eFlUZyIsImV4cCI6MTY0ODEzNDg2MX0.2U2s97fBpLZusxxae0Gwx7PI78YiVv1vw9UL1F6GfE8&service=proxsee&digest=05c5x4JJJwi6hlvl5V7N-wqcf3nJhfAtkvDIdVVH30o&ts=823981030","status":"Confirmation hearing for Supreme Court nominee Judge Ketanji Brown Jackson (Day 2)","broadcast_source":"livecms","available_for_replay":true,"user_id":"1060690","twitter_user_id":"15675138","user_display_name":"C-SPAN","username":"cspan","twitter_username":"cspan","profile_image_url":"https://pbs.twimg.com/profile_images/1107583584460857344/Ewo1E1vu_reasonably_small.png","state":"RUNNING","is_locked":false,"friend_chat":false,"has_moderation":true,"height":540,"width":960,"camera_rotation":0,"has_location":false,"lat":0.0,"lng":0.0,"total_watching":"11873","total_watched":"176851","start_ms":"1647953541642","ping_ms":"1647962052452","private_chat":false,"is_high_latency":true,"version":1167}},"events":{}}
```

关键词`chunk`、`m3u8`、`ts`。

```
#EXTM3U
#EXT-X-VERSION:6
#EXT-X-TARGETDURATION:3
#EXT-X-INDEPENDENT-SEGMENTS
#EXT-X-MEDIA-SEQUENCE:5834
#EXT-X-DISCONTINUITY-SEQUENCE:0
#EXT-X-START:TIME-OFFSET=0.01
#EXT-X-PROGRAM-DATE-TIME:2022-03-22T15:15:33.254Z
#EXTINF:2.000,
chunk_1647962129264366544_5834_a.ts?type=live
#EXT-X-PROGRAM-DATE-TIME:2022-03-22T15:15:35.261Z
#EXTINF:2.000,
```

使用`M3U8 finder and HLS player`插件可以找到真实播放链接，并且可以直接播放。
```
https://prod-ec-us-east-1.video.pscp.tv/Transcoding/v1/hls/5nGWql69wDF2KNG5Qo5bNSSbPJsLdLLBB-VswKnzatm069gn2GIMJtjICrb2F6v3xgCZPfONLQrzRcLuOwxYTg/transcode/us-east-1/periscope-replay-direct-prod-us-east-1-public/eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCIsInZlcnNpb24iOiIyIn0.eyJFbmNvZGVyU2V0dGluZyI6ImVuY29kZXJfc2V0dGluZ18zMjBwMzBfMTAiLCJIZWlnaHQiOjMyMCwiS2JwcyI6NjAwLCJUcmFuc2NvZGVBdWRpbyI6dHJ1ZSwiV2lkdGgiOjU2OH0.es_XpNv3J12hFXU4WrCwmH28GmToYAPDPdT_EjerHCU/dynamic_highlatency.m3u8?type=live
```

| ![有帮助的截图](/assets/WX20220322-233151.png) |
| :----------------------------------------: |
|          -        |

那么接下来的思路就是，怎么实现m3u8的语音识别。像带字幕的这种应该是使用的是`webvtt`应该也能截取并翻译。ffmpeg也支持推直播了。

```shell
ffmpeg -i video.mp4 -i subtitle.srt \
-preset slow -g 60 -sc_threshold 0 \
-map 0 -map 0 -map 0 -map 1 \
-s:v:0 640x360 -c:v:0 h264 -b:v:0 500k \
-s:v:1 854x480 -c:v:1 h264 -b:v:1 1000k \
-s:v:2 1280x720 -c:v:2 h264 -b:v:2 2000K \
-c:a copy -c:s webvtt \
-f hls -hls_playlist_type vod -var_stream_map "v:0,a:0 v:1,a:1 v:2,a:2" \
-master_pl_name master.m3u8 -hls_time 6 -hls_list_size 0 -hls_allow_cache 1 -start_number 1 \
-hls_segment_filename "output/hls/%v/seg-%d.ts" output/hls/%v/index.m3u8
```
来自：https://stackoverflow.com/questions/67663932/how-to-add-a-subtitle-to-an-hls-playlist-using-ffmpeg


未整理资料

https://aws.amazon.com/cn/about-aws/whats-new/2021/05/amazon-transcribe-improves-live-subtitling-partial-results-stabilization/  
https://github.com/luvletter2333/Live-SubTitle  
https://support.google.com/youtube/answer/3068031?hl=zh-Hans  


[1]: https://www.xfyun.cn/services/rtasr
[2]: https://www.xfyun.cn/doc/asr/rtasr/API.html
[3]: https://cloud.baidu.com/product/speech/realtime_asr
[4]: https://help.aliyun.com/document_detail/84428.html
[5]: https://support.google.com/chrome/answer/10538231?hl=en
[6]: https://www.android.com/accessibility/live-transcribe/
