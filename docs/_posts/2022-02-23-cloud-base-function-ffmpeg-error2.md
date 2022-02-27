---
layout: post
title:  "云函数transcode-video转非avi格式出错"
date:   2022-02-23 00:55:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

试用《[腾讯云部署流式转码应用][1]》的`transcode-video`(mp4转avi)，非常不稳定，里面正常时而不正常。

以下是日志，但是没有明显失败的原因。
```
START RequestId: d022792c-e00a-4d57-8de9-c4f9940304c2

Init Report RequestId: d022792c-e00a-4d57-8de9-c4f9940304c2 Coldstart: 2115ms (PullCode: 368ms InitRuntime: 298ms InitFunction: 1449ms) Memory: 3072MB MemUsage: 16.73MB

---------------------------start34234----------------------------

{"Records": [{"cos": {"cosBucket": {"appid": "1309725374", "cosRegion": "ap-shanghai", "name": "fanyi", "region": "sh", "s3Region": "ap-shanghai"}, "cosNotificationId": "unkown", "cosObject": {"key": "/1309725374/fanyi/video/inputs/HappyLunarNewYear.mp4", "meta": {"Content-Type": "video/mp4", "ETag": "\"eb6cf523ae4d528e72f2d11f3a91cd40\"", "x-cos-request-id": "NjIxNjY0YzhfYzMyNjgwOV8xMmEyXzNhNjBmNGY=", "x-cos-storage-class": "Standard"}, "size": 2561690, "url": "http://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/inputs/HappyLunarNewYear.mp4", "vid": ""}, "cosSchemaVersion": "1.0"}, "event": {"eventName": "cos:ObjectCreated:Put", "eventQueue": "qcs:0:scf:ap-shanghai:appid/1309725374:default.transcode-video-transcode-app-f20c4acc-dev.$DEFAULT", "eventSource": "qcs::cos", "eventTime": 1645634761, "eventVersion": "1.0", "reqid": 0, "requestParameters": {"requestHeaders": {"Authorization": "q-sign-algorithm=sha1&q-ak=AKID-dhPo4Og7uBq2t34ppMjo0jDX5IYSEk6hcsV-f8349TKPbswwcA3IwvNBut1Dq3n&q-sign-time=1645634577;1645638177&q-key-time=1645634577;1645638177&q-header-list=content-length;content-md5;x-cos-storage-class&q-url-param-list=&q-signature=485bd42af2db217a25ac5214526cac6349b23489"}, "requestSourceIP": "114.249.0.117"}, "reservedInfo": ""}}]}

---------------------------start222-------------------------

{'task': 'LOG TASK', 'index_group': 'HappyLunarNewYear.mp4-20220224004604', 'type': 'init', 'time_stamp': '2022-02-24 00:46:04', 'file': ('HappyLunarNewYear-20220224004604.mp4',), 'size': ('2.44M',), 'transcode_format': ('mp4',)}

create multipart upload, url=:https://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs//HappyLunarNewYear-20220224004604.mp4 ,headers=:{}

{'task': 'UPLOAD TASK', 'type': 'init', 'time_stamp': '2022-02-24 00:46:04', 'detail': {'Bucket': 'fanyi-1309725374', 'Key': 'video/outputs/HappyLunarNewYear-20220224004604.mp4', 'UploadId': '164563476406db170a4e7ec94165fe7f3fc982ed695418df6b34ced06444650b893dfd922a'}}

{'task': 'LOG TASK', 'index_group': 'HappyLunarNewYear.mp4-20220224004604', 'type': 'end', 'time_stamp': '2022-02-24 00:46:06', 'file': ('HappyLunarNewYear-20220224004604.mp4',), 'size': ('2.44M',), 'transcode_format': ('mp4',), 'transcode_cost_time': '2.2s', 'transcode_success': 'ffmpeg task failed'}

{'task': 'LOG TASK', 'index_group': 'HappyLunarNewYear.mp4-20220224004604', 'type': 'end', 'file': ('HappyLunarNewYear-20220224004604.mp4',), 'size': ('2.44M',), 'ffmpeg_log': ['ffmpeg version 87201e0 Copyright (c) 2000-2019 the FFmpeg developers', 'built with gcc 4.9.2 (Debian 4.9.2-10)', "configuration: --prefix=/root/work/ffmpeg-static/target --pkg-config-flags=--static --extra-cflags=-I/root/work/ffmpeg-static/target/include --extra-ldflags=-L/root/work/ffmpeg-static/target/lib --extra-libs='-lpthread -lm -lz' --extra-ldexeflags=-static --bindir=/root/work/ffmpeg-static/bin --enable-pic --enable-ffplay --enable-fontconfig --enable-frei0r --enable-gpl --enable-version3 --enable-libass --enable-libfribidi --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libopenjpeg --enable-libopus --enable-librtmp --enable-libsoxr --enable-libspeex --enable-libtheora --enable-libvidstab --enable-libvo-amrwbenc --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxvid --enable-libzimg --enable-nonfree --enable-openssl", 'libavutil      56. 22.100 / 56. 22.100', 'libavcodec     58. 35.100 / 58. 35.100', 'libavformat    58. 20.100 / 58. 20.100', 'libavdevice    58.  5.100 / 58.  5.100', 'libavfilter     7. 40.101 /  7. 40.101', 'libswscale      5.  3.100 /  5.  3.100', 'libswresample   3.  3.100 /  3.  3.100', 'libpostproc    55.  3.100 / 55.  3.100', "Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'https://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/inputs/HappyLunarNewYear.mp4?sign=q-sign-algorithm%3Dsha1%26q-ak%3DAKIDmHkVhG5sxVxfQU9JHR70gwkYvwLTGT8AoyxEWaLoXYxCifdUMM4UPgYPHH4g99kC%26q-sign-time%3D1645634704%3B1645677964%26q-key-time%3D1645634704%3B1645677964%26q-header-list%3D%26q-url-param-list%3D%26q-signature%3D197e7da1eaeb98c3c98bdceb7b4795c370aa111d&x-cos-security-token=SaVwisZpmFztILZUoU8Xiav41KXiu6Va2acc754bddb9da7e8cafe1ef05d68ae9qWt5tbg82EXQSuaJPWXFbehY50XJOW8_ZMl2hUieG54u1m7QyvXcFbybn2XCBX0Hqz5jRNgsOy7GhWtKkIgEu4ZEhVwMhdfU3KuV0QC70fXF4AulXZCcmLsLO8QWdulk_j89ySelOEeNokrclZDO2RcVuBVsi_UtKsef_lcEdrSj-wGw99y7RpQZXtUSGMvhhLbugD2WoNqaL6Ywd5lo4NkdJrKzhkOXgU8-8VD7w_OnLSTyhdN_n88-MrFfPfnBOX5rUCjxhwXBHj7XY3Ywpk4qSLqEjLlDYR9kytq3yqqXBRBDjNZPMoUlizdANAimkUPSM3CWBYmnj-Zbxgbb_dOy-lhNL_CFCz3crN5E7qU':", 'Metadata:', 'major_brand     : mp42', 'minor_version   : 0', 'compatible_brands: mp42mp41iso4', 'creation_time   : 2022-02-02T05:05:03.000000Z', 'Duration: 00:01:01.02, start: 0.000000, bitrate: 335 kb/s', 'Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p(tv, bt709), 720x720, 201 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 48k tbc (default)', 'Metadata:', 'creation_time   : 2022-02-02T05:05:03.000000Z', 'handler_name    : Vireo Eyes v2.7.3', 'encoder         : AVC Coding', 'Stream #0:1(und): Audio: aac (LC) (mp4a / 0x6134706D), 44100 Hz, stereo, fltp, 128 kb/s (default)', 'Metadata:', 'creation_time   : 2022-02-02T05:05:03.000000Z', 'handler_name    : Vireo Ears v2.7.3', 'Stream mapping:', 'Stream #0:0 -> #0:0 (h264 (native) -> h264 (libx264))', 'Stream #0:1 -> #0:1 (aac (native) -> aac (native))']}

{'task': 'LOG TASK', 'index_group': 'HappyLunarNewYear.mp4-20220224004604', 'type': 'end', 'file': ('HappyLunarNewYear-20220224004604.mp4',), 'size': ('2.44M',), 'ffmpeg_log': ['Press [q] to stop, [?] for help', '[libx264 @ 0x3f6e000] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX FMA3 BMI2 AVX2 AVX512', '[libx264 @ 0x3f6e000] profile Progressive High, level 3.1, 4:2:0, 8-bit', '[libx264 @ 0x3f6e000] 264 - core 157 - H.264/MPEG-4 AVC codec - Copyleft 2003-2019 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=23 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00', '[mp4 @ 0x3f59280] muxer does not support non seekable output', 'Could not write header for output file #0 (incorrect codec parameters ?): Invalid argument', 'Error initializing output stream 0:0 --', '[aac @ 0x3f6a540] Qavg: 65536.000', '[aac @ 0x3f6a540] 2 frames left in the queue on closing']}

complete multipart upload, url=:https://fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs//HappyLunarNewYear-20220224004604.mp4 ,headers=:{}

<?xml version='1.0' encoding='utf-8' ?>

<Error>

<Code>MalformedXML</Code>

<Message>The XML you provided was not well-formed or did not validate against our published schema.</Message>

<Resource>fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs/HappyLunarNewYear-20220224004604.mp4</Resource>

<RequestId>NjIxNjY0Y2VfNTI0NzIyMDlfOGYwOV80OGQyMGE0</RequestId>

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

<Resource>fanyi-1309725374.cos.ap-shanghai.myqcloud.com/video/outputs/HappyLunarNewYear-20220224004604.mp4</Resource>

<RequestId>NjIxNjY0Y2VfNTI0NzIyMDlfOGYwOV80OGQyMGE0</RequestId>

<TraceId>OGVmYzZiMmQzYjA2OWNhODk0NTRkMTBiOWVmMDAxODc0OWRkZjk0ZDM1NmI1M2E2MTRlY2MzZDhmNmI5MWI1OTI5MWRkM2I1ZDU3ZWE5Y2YzNDYzZTEzY2JlMjU3NDQ0MTAzNGQyNTFiM2NjYjgzZjgwNGNmNTRjMmM3OWNhZGM=</TraceId>

</Error>

---------------------------end-------------------------

Response RequestId:d022792c-e00a-4d57-8de9-c4f9940304c2 RetMsg:{"code": 200, "Msg": "success"}

END RequestId:d022792c-e00a-4d57-8de9-c4f9940304c2

Report RequestId:d022792c-e00a-4d57-8de9-c4f9940304c2 Duration:2607ms Memory:3072MB MemUsage:29.789383MB
```

结论：输出格式设置为flv/mp4格式等都会报错，这是什么原因呢？

[1]: /cloud/2022/02/22/cos-video-convert-again.html
