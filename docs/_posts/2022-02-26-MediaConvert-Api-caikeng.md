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

## 1.1 先使用Postman
从[MediaConvert create resources collection][3]找到Postman专用集合，导入到Postman APP中。

| ![有帮助的截图](/assets/WX20220226-175140.png) |
| :----------------------------------------: |
|          Postman测试集合         |

## 1.2 导入Postman
`File` -> `Import...`，选择`Raw text`将内容贴入。

| ![有帮助的截图](/assets/WX20220226-175743.png) |
| :----------------------------------------: |
|          Postman测试集合         |

导入成功效果

| ![有帮助的截图](/assets/WX20220226-181656.png) |
| :----------------------------------------: |
|          导入成功效果         |

### 导入失败处理方法
如果处理以下导入失败的提示，将v1版转换为v2版重新再导。[converting-postman-collections-from-v1-to-v2][6]
```
1 invalid import format(s)
Postman Collection Format v1 is no longer supported and can not be imported directly. You may
convert your collection to Format v2
 and try importing again.
```

## 1.3 Postman测试

### 填写Auth参数

| ![有帮助的截图](/assets/WX20220226-181815.png) |
| :----------------------------------------: |
|          Postman测试集合         |

### 填写Body参数
不要使用默认的，而使用图形化执行成功的任务导出Json。

从[图形化任务中][4]导出JSON

| ![有帮助的截图](/assets/WX20220226-182626.png) |
| :----------------------------------------: |
|          查看成功的JSON         |

粘贴后效果

| ![有帮助的截图](/assets/WX20220226-181842.png) |
| :----------------------------------------: |
|          粘贴后效果         |


### 成功效果

| ![有帮助的截图](/assets/WX20220226-181952.png) |
| :----------------------------------------: |
|          Postman测试集合         |

从网页控制台上也能看到此任务。

# 2.使用Python脚本

# 官方例子
[AWS Elemental MediaConvert CreateJob Example Using the SDK for Python][5]
```python
import json
import boto3

# Create MediaConvert client
mediaconvert_client = boto3.client('mediaconvert', endpoint_url='https://abcd1234.mediaconvert.us-west-2.amazonaws.com')

# Load job.json from disk and store as Python object: job_object
with open("job.json", "r") as jsonfile:
    job_object = json.load(jsonfile)

# Create MediaConvert job by unpacking the arguments from job_object. The job object contains the required parameters
# for create_job. Pass these to create_job using Python's ** argument unpacking syntax.
mediaconvert_client.create_job(**job_object)
```

# 实际成功的例子
```python
import json
import boto3

AWS_ACCESS_KEY_ID = 'AKIA.......J7UM'
AWS_AECRET_ACCESS_KEY = 'xBKQjytY.......+v8L5H8'
REGION_NAME = 'us-west-2'

# Create MediaConvert client
mediaconvert_client = boto3.client('mediaconvert',
                                     aws_access_key_id = AWS_ACCESS_KEY_ID,
                                     aws_secret_access_key = AWS_AECRET_ACCESS_KEY,
                                     region_name = REGION_NAME,
                                     endpoint_url = 'https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com',
                                   )

# Load job.json from disk and store as Python object: job_object
with open("job.json", "r") as jsonfile:
    job_object = json.load(jsonfile)

# Create MediaConvert job by unpacking the arguments from job_object. The job object contains the required parameters
# for create_job. Pass these to create_job using Python's ** argument unpacking syntax.
mediaconvert_client.create_job(**job_object)
```
其中`job.json`使用postman已经成功的实例即可，也还是图形化任务导出的json文件。

# 3.一些杂项待整理

## 关于endpoints

| OK | 来源 | 报错 | 结论  | 链接 |
| :---- | :---- | :---- | :----  | :---- |
| NO | [docs推荐1][2] | Unable to determine service/operation name to be authorized | 不成功别用 | https://mediaconvert.us-west-2.amazonaws.com/2017-08-29/endpoints |
| NO | 添加PATH | SSL validation failed for EOF occurred in violation of protocol| PATH错了 | https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs |
| OK | 去掉PATH | 'HTTPStatusCode': 201 |  使用工具获取的，正确 | https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com |
| NO | [docs推荐2][1] | SSL validation failed for | 看错，并非ID  | https://238417667751.mediaconvert.us-west-2.amazonaws.com |


写个Chrome插件实现postman api由v1转为v2。
https://docs.aws.amazon.com/mediaconvert/latest/ug/postman-collection-files.html#postman-collection-POST
https://learning.postman.com/docs/getting-started/importing-and-exporting-data/#converting-postman-collections-from-v1-to-v2

## Postman遇到
```
Credential should be scoped to a valid region, not 'us-west-'.
```
解决方案是`Authorization`下的`AWS Region`写错了。

## Postman遇到
```
Error: Client network socket disconnected before secure TLS connection was established
```
解决方案是网址由`https://238417667751.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`改为`https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`。

## Postman遇到
```json
{
    "errorType": "BadRequestException",
    "httpStatus": 400,
    "requestId": "9acb2feb-571d-4048-868d-4c2071c4847d",
    "message": "You must use the customer-specific endpoint 'https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com' for this operation.",
    "settingsValidationErrorsJsonBlob": ""
}
```
解决方案是网址由`https://mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`改为`https://mlboolfjb.mediaconvert.us-west-2.amazonaws.com/2017-08-29/jobs`。

## Postman遇到
```
Missing Authentication Token
```
解决方案是`Authorization`下选`AWS Signature`。

```
Error: getaddrinfo ENOTFOUND 238417667751.mediaconvert.us-west-2.amazonaws.com
```

```
An error occurred (AccessDeniedException) when calling the CreateJob operation: Unable to determine service/operation name to be authorized
```


[1]: https://docs.aws.amazon.com/mediaconvert/latest/apireference/python.html
[2]: https://docs.aws.amazon.com/mediaconvert/latest/apireference/getting-started.html
[3]: https://docs.aws.amazon.com/mediaconvert/latest/ug/postman-collection-files.html#postman-collection-POST
[4]: https://us-west-2.console.aws.amazon.com/mediaconvert/home?region=us-west-2#/jobs/list
[5]: https://docs.aws.amazon.com/mediaconvert/latest/apireference/python.html
[6]: https://learning.postman.com/docs/getting-started/importing-and-exporting-data/#converting-postman-collections-from-v1-to-v2
