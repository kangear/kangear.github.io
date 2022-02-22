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
```console
% sls init transcode-app

serverless ⚡components

- 项目 "transcode-app" 已在当前目录成功创建
- 执行 "cd transcode-app && serverless deploy" 部署应用

transcode-app › 创建成功
%
```

# 创建API
https://console.cloud.tencent.com/cam/capi

| ![有帮助的截图](/assets/WX20220201-112153.png) |
| :----------------------------------------: |
|          *原问题*          |

# 创建角色transcodeRole

| ![有帮助的截图](/assets/WX20220222-093809.png) |
| :----------------------------------------: |
|          *原问题*          |

来自：https://cloud.tencent.com/document/product/583/51451#role

# 报错
报错`Cannot read property 'Namespace' of null`
```console
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

# 部署成功
按照如下修改
```diff
diff --git a/transcode/serverless.yml b/transcode/serverless.yml
index 75793ee..834661c 100644
--- a/transcode/serverless.yml
+++ b/transcode/serverless.yml
@@ -13,13 +13,13 @@ inputs:
   timeout: 43200 # 函数执行超时时间, 单位秒, 即本demo目前最大支持12h运行时长
   region: ${env:REGION} # 函数区域，统一在环境变量中定义
   asyncRunEnable: true # 开启长时运行
-  cls: # 函数日志
-    logsetId: ${output:${stage}:${app}:cls-video.logsetId}  # cls日志集 cls-video为cls组件的实例名称
-    topicId: ${output:${stage}:${app}:cls-video.topicId}  # cls日志主题
+  # cls: # 函数日志
+  #   logsetId: ${output:${stage}:${app}:cls-video.logsetId}  # cls日志集 cls-video为cls组件的实例名称
+  #   topicId: ${output:${stage}:${app}:cls-video.topicId}  # cls日志主
```

```console
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

%
```
总结，其实就是A依赖B，B依赖A的问题。部署成功之后再放开注释就可以了。Linux启动时也会有这种依赖问题，他们是使用systemd，可以看看大师的文章《[LINUX PID 1 和 SYSTEMD][1]》。如果云函数的部署能简单到`真一键`，cos代创建，sls代创建，AppKey代创建会让初学都更快上手，初学者未来就大学者。

# 试用
试用无任何反应，技术支持给的反馈是内部问题`配置下发延迟，开发同学在看`。继续等一下结果吧。


[1]: https://coolshell.cn/articles/17998.html
