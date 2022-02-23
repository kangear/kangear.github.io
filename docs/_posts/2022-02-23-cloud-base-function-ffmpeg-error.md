---
layout: post
title:  "云函数中的ffmpeg执行失败但无相关日志"
date:   2022-02-22 22:55:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

基于《[腾讯云部署流式转码应用][1]》的`transcode-video`修改了一点，将视频和一个字幕文件合成。此命令在电脑上执行正常，推到云函数上就失败，但是无相关失败的日志，导致无法定位。

```diff
diff --git a/transcode/serverless.yml b/transcode/serverless.yml
index 75793ee..a3a3524 100644
--- a/transcode/serverless.yml
+++ b/transcode/serverless.yml
@@ -19,16 +19,16 @@ inputs:
   environment:
     variables:  # 转码参数
       REGION: ${env:REGION} # 输出桶区域
       DST_PATH: video/outputs/ # 输出桶路径
       DST_FORMAT: avi # 转码生成格式
-      FFMPEG_CMD: ffmpeg -i {input} -y -f {dst_format} {output}  # 转码基础命令，您可自定义配置，但必须包含ffmpeg配置参数和格式化部分，否则会造成转码任务失败。
+      FFMPEG_CMD: ffmpeg -i {input} -y -vf subtitles=subtitles.srt HappyNewYear_zh.srt -f {dst_format} {output}  # 转码基础命令，您可自定义配置，但必须包含ffmpeg配置参数和格式化部分，否则会造成转码任务失败。
       FFMPEG_DEBUG: 1 # 是否输出ffmpeg日志 0为不输出 1为输出
       TZ: Asia/Shanghai # cls日志输出时间的时区

```

以下是日志，但是没有明显失败的原因。
```
START RequestId: 34fbefe1-5550-4159-873d-e69828ad095c

Init Report RequestId: 34fbefe1-5550-4159-873d-e69828ad095c Coldstart: 2150ms (PullCode: 427ms InitRuntime: 267ms InitFunction: 1456ms) Memory: 3072MB MemUsage: 16.55MB

---------------------------start----------------------------

{"Records": [{"cos": {"cosBucket": {"appid": "1309725374", "cosRegion": "ap-shanghai", "name": "fanyi", "region": "sh", "s3Region": "ap-shanghai"}, "cosNotificationId": "unkown", "cosObject": {"key": "/1309725374/fanyi/video/inputs/HappyLunarNewYear.mp4", "meta": {"Content-Type": "video/mp4", "ETag": "\"eb6cf523ae4d528e72f2d11f3a91cd40\"", "x-cos-request-id": "NjIxNjIzZDRfM2JkMzc2MWVfOWI4OF82NWIzOGIw", "x-cos-storage-class": "Standard"}, "size": 2561690, "url": "http://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/inputs/HappyLunarNewYear.mp4", "vid": ""}, "cosSchemaVersion": "1.0"}, "event": {"eventName": "cos:ObjectCreated:Put", "eventQueue": "qcs:0:scf:ap-shanghai:appid/1309725374:default.transcode-video-transcode-app-f20c4acc-dev.$DEFAULT", "eventSource": "qcs::cos", "eventTime": 1645618133, "eventVersion": "1.0", "reqid": 0, "requestParameters": {"requestHeaders": {"Authorization": "q-sign-algorithm=sha1&q-ak=AKIDQqMyQ7Md9I15mG1SNJ7vRufqlfseHiLXRuzpwYknTN-4PTKOE6SZkzBHbMaAdXKm&q-sign-time=1645618132;1645621732&q-key-time=1645618132;1645621732&q-header-list=content-length;content-md5;x-cos-storage-class&q-url-param-list=&q-signature=601a1a3014c2d12334ba6124a432382b1e79e866"}, "requestSourceIP": "123.120.5.134"}, "reservedInfo": ""}}]}

---------------------------start222-------------------------

{'task': 'LOG TASK', 'index_group': 'HappyLunarNewYear.mp4-20220223200856', 'type': 'init', 'time_stamp': '2022-02-23 20:08:56', 'file': ('HappyLunarNewYear-20220223200856.avi',), 'size': ('2.44M',), 'transcode_format': ('avi',)}

create multipart upload, url=:https://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs//HappyLunarNewYear-20220223200856.avi ,headers=:{}

{'task': 'UPLOAD TASK', 'type': 'init', 'time_stamp': '2022-02-23 20:08:56', 'detail': {'Bucket': 'fanyi-1309725374', 'Key': 'video/outputs/HappyLunarNewYear-20220223200856.avi', 'UploadId': '164561813637ec880d30e1d6a601c25964a3ef58a3aaef9bd8b359e79056299ad3535f2108'}}

{'task': 'LOG TASK', 'index_group': 'HappyLunarNewYear.mp4-20220223200856', 'type': 'end', 'time_stamp': '2022-02-23 20:08:56', 'file': ('HappyLunarNewYear-20220223200856.avi',), 'size': ('2.44M',), 'transcode_format': ('avi',), 'transcode_cost_time': '0.3s', 'transcode_success': 'ffmpeg task failed'}

{'task': 'LOG TASK', 'index_group': 'HappyLunarNewYear.mp4-20220223200856', 'type': 'end', 'file': ('HappyLunarNewYear-20220223200856.avi',), 'size': ('2.44M',), 'ffmpeg_log': ['ffmpeg version 87201e0 Copyright (c) 2000-2019 the FFmpeg developers', 'built with gcc 4.9.2 (Debian 4.9.2-10)', "configuration: --prefix=/root/work/ffmpeg-static/target --pkg-config-flags=--static --extra-cflags=-I/root/work/ffmpeg-static/target/include --extra-ldflags=-L/root/work/ffmpeg-static/target/lib --extra-libs='-lpthread -lm -lz' --extra-ldexeflags=-static --bindir=/root/work/ffmpeg-static/bin --enable-pic --enable-ffplay --enable-fontconfig --enable-frei0r --enable-gpl --enable-version3 --enable-libass --enable-libfribidi --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libopenjpeg --enable-libopus --enable-librtmp --enable-libsoxr --enable-libspeex --enable-libtheora --enable-libvidstab --enable-libvo-amrwbenc --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxvid --enable-libzimg --enable-nonfree --enable-openssl", 'libavutil      56. 22.100 / 56. 22.100', 'libavcodec     58. 35.100 / 58. 35.100', 'libavformat    58. 20.100 / 58. 20.100', 'libavdevice    58.  5.100 / 58.  5.100', 'libavfilter     7. 40.101 /  7. 40.101', 'libswscale      5.  3.100 /  5.  3.100', 'libswresample   3.  3.100 /  3.  3.100', 'libpostproc    55.  3.100 / 55.  3.100', "Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'https://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/inputs/HappyLunarNewYear.mp4?sign=q-sign-algorithm%3Dsha1%26q-ak%3DAKIDrqAgl7Yg4wzLRNZluFGNi13HKYxA8gyXB2v9i2A8GFjkES2YERO93BO7olgt3Bj4%26q-sign-time%3D1645618076%3B1645661336%26q-key-time%3D1645618076%3B1645661336%26q-header-list%3D%26q-url-param-list%3D%26q-signature%3Dc93f3f9c84dfb998686c0732583ad00bdb12a2eb&x-cos-security-token=qS0EsZw7xMe4FTqmiF0pC8xkwtp8vKja2fb12ad9cbbaeb4d1b50d70f9f68f227rghteo_skPJv-68gwOJxOuZnROd6J0YrK4HK2wPEbO91JUAwk3jCP3j7du-OCxrTgx21M4zv4O8foI7qHtOM1-DEXFPrX_u-qGZ-4ZQdgd55miYXSrHk15zhsbsfELL2B1U80XL_M6fNY78681SgONwlleGlwYyzjGT-ehr1BZvxgVvQHv3FIqViASjJDB1gwTbGcjgrUITguHUUzG2X-c9AFZ6dsCVl3oALf_eVrMKmi84-VDtvmbxCFoqc9ERyMWHQnAleJEKI-tWFjdh6CnoQMiyixfV7PGHAnWLMDZiI_Yb6qP6drYwzbUTQXuxbsuFOfBAU1K4-owKQWI8CY6xPBcqzzY0WHOj9beZ3dW8':", 'Metadata:', 'major_brand     : mp42', 'minor_version   : 0', 'compatible_brands: mp42mp41iso4', 'creation_time   : 2022-02-02T05:05:03.000000Z', 'Duration: 00:01:01.02, start: 0.000000, bitrate: 335 kb/s', 'Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p(tv, bt709), 720x720, 201 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 48k tbc (default)', 'Metadata:', 'creation_time   : 2022-02-02T05:05:03.000000Z', 'handler_name    : Vireo Eyes v2.7.3', 'encoder         : AVC Coding', 'Stream #0:1(und): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 128 kb/s (default)', 'Metadata:', 'creation_time   : 2022-02-02T05:05:03.000000Z', 'handler_name    : Vireo Ears v2.7.3', "Output #0, srt, to 'HappyNewYear_zh.srt':"]}

complete multipart upload, url=:https://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs//HappyLunarNewYear-20220223200856.avi ,headers=:{}

<?xml version='1.0' encoding='utf-8' ?>

<Error>

<Code>MalformedXML</Code>

<Message>The XML you provided was not well-formed or did not validate against our published schema.</Message>

<Resource>fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs/HappyLunarNewYear-20220223200856.avi</Resource>

<RequestId>NjIxNjIzZDhfOWJjYjEwOV8zNzg3ZF80OGEyZDE1</RequestId>

<TraceId>OGVmYzZiMmQzYjA2OWNhODk0NTRkMTBiOWVmMDAxODc0OWRkZjk0ZDM1NmI1M2E2MTRlY2MzZDhmNmI5MWI1OTI5MWRkM2I1ZDU3ZWE5Y2YzNDYzZTEzY2JlMjU3NDQ0MTAzNGQyNTFiM2NjYjgzZjgwNGNmNTRjMmM3OWNhZGM=</TraceId>

</Error>

Traceback (most recent call last):

  File "/var/user/index.py", line 130, in file_upload_ffmpeg_task

    MultipartUpload={'Part': part_list}

  File "/var/lang/python3/lib/python3.6/site-packages/qcloud_cos_v5/cos_client.py", line 740, in complete_multipart_upload

    params=params)

  File "/var/lang/python3/lib/python3.6/site-packages/qcloud_cos_v5/cos_client.py", line 247, in send_request

    raise CosServiceError(method, msg, res.status_code)

qcloud_cos_v5.cos_exception.CosServiceError: <?xml version='1.0' encoding='utf-8' ?>

<Error>

<Code>MalformedXML</Code>

<Message>The XML you provided was not well-formed or did not validate against our published schema.</Message>

<Resource>fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs/HappyLunarNewYear-20220223200856.avi</Resource>

<RequestId>NjIxNjIzZDhfOWJjYjEwOV8zNzg3ZF80OGEyZDE1</RequestId>

<TraceId>OGVmYzZiMmQzYjA2OWNhODk0NTRkMTBiOWVmMDAxODc0OWRkZjk0ZDM1NmI1M2E2MTRlY2MzZDhmNmI5MWI1OTI5MWRkM2I1ZDU3ZWE5Y2YzNDYzZTEzY2JlMjU3NDQ0MTAzNGQyNTFiM2NjYjgzZjgwNGNmNTRjMmM3OWNhZGM=</TraceId>

</Error>

---------------------------end-------------------------

Response RequestId:34fbefe1-5550-4159-873d-e69828ad095c RetMsg:{"code": 200, "Msg": "success"}

END RequestId:34fbefe1-5550-4159-873d-e69828ad095c

Report RequestId:34fbefe1-5550-4159-873d-e69828ad095c Duration:821ms Memory:3072MB MemUsage:21.402641MB
```


[1]: /cloud/2022/02/22/cos-video-convert-again.html
