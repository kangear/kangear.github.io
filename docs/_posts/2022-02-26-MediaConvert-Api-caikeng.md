---
layout: post
title:  "MediaConvert API踩坑"
date:   2022-02-26 17:47:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

在界面上操作终于成功，给一个MP4文件添加了Burn in的字幕。下面试用API进行一次操作，结果摸索一天不能成功。以下是操作完成的正确步骤

# 1.先使用Postman
从[MediaConvert create resources collection][3]找到Postman专用集合，导入到Postman APP中。

| ![有帮助的截图](/assets/WX20220226-175140.png) |
| :----------------------------------------: |
|          Postman测试集合         |

# 2.导入Postman
`File` -> `Import...`，选择`Raw text`将内容贴入。

| ![有帮助的截图](/assets/WX20220226-175743.png) |
| :----------------------------------------: |
|          Postman测试集合         |

# 关于endpoints

| OK | 来源 | 报错 | 结论  | 链接 |
| :---- | :---- | :---- | :----  | :---- |
| NO | [docs推荐1][2] | Unable to determine service/operation name to be authorized | 不成功别用 | https://mediaconvert.us-west-2.amazonaws.com/2017-08-29/endpoints |
| NO | 添加PATH | SSL validation failed for EOF occurred in violation of protocol| PATH错了 | https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs |
| OK | 去掉PATH | 'HTTPStatusCode': 201 |  使用工具获取的，正确 | https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com |
| NO | [docs推荐2][1] | SSL validation failed for | 看错，并非ID  | https://238417667751.mediaconvert.us-west-2.amazonaws.com |


写个Chrome插件实现postman api由v1转为v2。
https://docs.aws.amazon.com/mediaconvert/latest/ug/postman-collection-files.html#postman-collection-POST
https://learning.postman.com/docs/getting-started/importing-and-exporting-data/#converting-postman-collections-from-v1-to-v2

# Postman遇到
```
Credential should be scoped to a valid region, not 'us-west-'.
```
解决方案是`Authorization`下的`AWS Region`写错了。

# Postman遇到
```
Error: Client network socket disconnected before secure TLS connection was established
```
解决方案是网址由`https://238417667751.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`改为`https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`。

# Postman遇到
```
{
    "errorType": "BadRequestException",
    "httpStatus": 400,
    "requestId": "9acb2feb-571d-4048-868d-4c2071c4847d",
    "message": "You must use the customer-specific endpoint 'https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com' for this operation.",
    "settingsValidationErrorsJsonBlob": ""
}
```
解决方案是网址由`https://mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`改为`https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`。

# Postman遇到
```
Missing Authentication Token
```
解决方案是`Authorization`下选`AWS Signature`。

# Postman遇到
```
503Service Unavailable
```
解决方案是网址由`238417667751.mediaconvert.us-west-2.amazonaws.com`改为`https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`。






```
Error: getaddrinfo ENOTFOUND 238417667751.mediaconvert.us-west-2.amazonaws.com
```


```
https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs
```


```
An error occurred (AccessDeniedException) when calling the CreateJob operation: Unable to determine service/operation name to be authorized
```


[1]: https://docs.aws.amazon.com/mediaconvert/latest/apireference/python.html
[2]: https://docs.aws.amazon.com/mediaconvert/latest/apireference/getting-started.html
[3]: https://docs.aws.amazon.com/mediaconvert/latest/ug/postman-collection-files.html#postman-collection-POST
