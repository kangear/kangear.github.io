---
layout: post
title:  "实践:腾讯云部署流式转码应用 AGAIN"
date:   2022-02-22 22:55:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

官方教程：https://cloud.tencent.com/document/product/583/51451

# 安装transcode-app
```shell-session
% sls init transcode-app

serverless ⚡components

- 项目 "transcode-app" 已在当前目录成功创建
- 执行 "cd transcode-app && serverless deploy" 部署应用

transcode-app › 创建成功
```

# 创建API
https://console.cloud.tencent.com/cam/capi

# 创建角色transcodeRole
来自：https://cloud.tencent.com/document/product/583/51451#role

# 报错
报错`Cannot read property 'Namespace' of null`
```shell-session
% sls deploy

serverless ⚡components

cls-video: Response code 403 (Forbidden) (reqId: NjIxNDQyOTlfMF85YmI2XzE2MGRiYTBi)

  帮助文档: https://www.serverless.com/cn/framework/docs/
  BUG提交: https://github.com/serverless/serverless-tencent/issues
  问答社区: https://github.com/serverless/serverless-tencent/discussions

transcode-video: Cannot read property 'Namespace' of null

  帮助文档: https://www.serverless.com/cn/framework/docs/
  BUG提交: https://github.com/serverless/serverless-tencent/issues
  问答社区: https://github.com/serverless/serverless-tencent/discussions

29s › transcode-app › 已成功 部署组件0个，失败2个

  帮助文档: https://www.serverless.com/cn/framework/docs/
  BUG提交: https://github.com/serverless/serverless-tencent/issues
  问答社区: https://github.com/serverless/serverless-tencent/discussions
```

# 成功
```diff
diff --git a/transcode/src/index.py b/transcode/src/index.py
index 994ae19..f5ec85f 100644
--- a/transcode/src/index.py
+++ b/transcode/src/index.py
@@ -10,8 +10,8 @@ import traceback
 import subprocess
 import threading

-from qcloud_cos_v5 import CosConfig
-from qcloud_cos_v5 import CosS3Client
+# from qcloud_cos_v5 import CosConfig
+# from qcloud_cos_v5 import CosS3Client

 # 控制log输出级别
 logger = logging.getLogger()
```

```shell-session
% sls deploy

serverless ⚡components

cls-video 部署成功:
---------------------------------------------
region:   ap-shanghai
name:     cls-log
topic:    video-log
logsetId: 3577c3a6-9009-48ca-ba02-2f74324294f5
topicId:  56490c54-1587-4f63-a23f-da3bfaace0f5
period:   7

transcode-video 部署成功:
---------------------------------------------
type:         event
functionName: transcode-video-transcode-app-f20c4acc-dev
code:
  bucket: sls-cloudfunction-ap-shanghai-code
  object: /scf_component_dc4leui-1645495862.zip
description:  This is a function in transcode-app-f20c4acc application
namespace:    default
runtime:      Python3.6
handler:      index.main_handler
memorySize:   3072
lastVersion:  $LATEST
traffic:      1
triggers:
  -
    NeedCreate:       true
    AddTime:          2022-02-22 10:11:15
    AvailableStatus:  
    BindStatus:       
    CustomArgument:   
    Enable:           1
    ModTime:          2022-02-22 10:11:15
    ResourceId:       
    TriggerAttribute:
    TriggerDesc:      {"bucketUrl":"fanyi-1309725374.cos.ap-shanghai.myqcloud.com","event":"cos:ObjectCreated:*","filter":{"Prefix":"video/inputs/","Suffix":""}}
    TriggerName:      cos_c8a4cgkuj59qa391t20g
    Type:             cos
    Qualifier:        $DEFAULT

17s › transcode-app › 已成功部署组件2个

**************************************************
邀请您填写调查问卷: https://www.surveymonkey.com/r/slcusage
**************************************************

yuanbaokang@mac transcode-app %
```
