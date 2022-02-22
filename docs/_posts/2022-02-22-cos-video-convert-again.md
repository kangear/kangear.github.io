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
