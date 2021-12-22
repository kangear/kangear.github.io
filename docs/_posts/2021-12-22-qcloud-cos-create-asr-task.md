---
layout: post
title:  "腾讯云对象存储的《提交语音识别任务》描述得不够详细"
date:   2021-12-22 17:00:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

副标题：对象存储《提交语音识别任务》易用性优化

# 前言
我需要实现小程序`创建COS语音识别任务`的功能，参考了官方教程[提交语音识别任务][1]，文档是被归类到`数据万象`下的，描述比较简单，又看到了比较痛苦的`签名`，而且没有一个完整的demo。

官方教程链接：https://cloud.tencent.com/document/product/460/46228

# 控制台用起来
这里截图表示对应控制台的哪个功能，方便快速了解。就是这个功能：

| ![有帮助的截图](/assets/WX20211222-172004.png) |
| :----------------------------------------: |
|          *控制台创建任务*          |


# 问题
这个`COS语音识别功用`算是跨界，一边在`COS`，一边是`数据万象`。代码实现创建任务的话有以下问题，比如COS的SDK比较丰富，但是不包含`创建语音识别任务`这个功能；而`数据万象`的文档又只是简单描述，处于两不管的状态，让人觉得很无奈。

# COS的SDK

地址：https://github.com/tencentyun/cos-wx-sdk-v5

可以很简单的实现上传文件到COS中，所谓简单是指SDK和Demo比较丰富，不用户作很复杂的`签名`工作就可以跑起来。如下：

```js
// 存储桶名称，由bucketname-appid 组成，appid必须填入，可以在COS控制台查看存储桶名称。 https://console.cloud.tencent.com/cos5/bucket
var Bucket = 'test-1250000000';
// 存储桶Region可以在COS控制台指定存储桶的概览页查看 https://console.cloud.tencent.com/cos5/bucket/
// 关于地域的详情见 https://cloud.tencent.com/document/product/436/6224
var Region = 'ap-guangzhou';

// 初始化实例
var cos = new COS({
    getAuthorization: function (options, callback) {
        // 异步获取签名
        wx.request({
            url: 'https://example.com/sts.php', // 步骤二提供的签名接口
            data: {
                Method: options.Method,
                Key: options.Key
            },
            dataType: 'text',
            success: function (result) {
                var data = result.data;
                callback({
                    TmpSecretId: data.credentials && data.credentials.tmpSecretId,
                    TmpSecretKey: data.credentials && data.credentials.tmpSecretKey,
                    XCosSecurityToken: data.credentials && data.credentials.sessionToken,
                    ExpiredTime: data.expiredTime,
                });
            }
        });
    }
});

// 选择文件
wx.chooseImage({
    count: 1, // 默认9
    sizeType: ['original'], // 可以指定是原图还是压缩图，默认用原图
    sourceType: ['album', 'camera'], // 可以指定来源是相册还是相机，默认二者都有
    success: function (res) {
        var filePath = res.tempFiles[0].path;
        var filename = filePath.substr(filePath.lastIndexOf('/') + 1);
        cos.postObject({
            Bucket: Bucket,
            Region: Region,
            Key: filename,
            FilePath: filePath,
            onProgress: function (info) {
                console.log(JSON.stringify(info));
            }
        }, function (err, data) {
            console.log(err || data);
        });
    }
});
```


# 回到数据万象

| ![有帮助的截图](/assets/WX20211222-171154.png) |
| :----------------------------------------: |
|          *说明*          |

使用COS的SDK让你摆脱了`签名`计算，当你准备使用`创建语音识别任务`功能时，你不得不继续回到原始人状态，还得研究如何计算`签名`，这种心情让人难以理解。更关键的是没有一个demo代码。

# 结论
在COS的SDK上加上创建语音识别任务的功能，或者把万象数据下的创建语音识别任务的demo搞得全面一点，让快速上手。


[1]: https://cloud.tencent.com/document/product/460/46228
