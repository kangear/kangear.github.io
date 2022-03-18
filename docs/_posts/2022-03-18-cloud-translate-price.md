---
layout: post
title:  "云厂商翻译大比拼"
date:   2022-03-18 21:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---


# 文本翻译对比

| 厂家 | 免费额度 | 超出部分 | QPS（每秒访问量） |
| :---- | :---- | :---- | :---- |
| [百度][1] | 每月200万字 | 49元/百万字符  | 10 |
| [DeepL Free][5] | 每月50万字 |            -     | - |
| [微信翻译][6] | 提供英汉互翻，每次最大600Byte | -     | - |
| [微信同声传译][6]| 后台限制1000字节大小 | -     | - |

# 语音翻译

| 厂家 | 免费额度 | 超出部分 | QPS（每秒访问量） |
| :---- | :---- | :---- | :---- |
| [百度][2] | 每月可享1万次免费调用次数 | 0.025/次  | - |

# 同传

| 厂家 | 免费额度 | 超出部分 | QPS（每秒访问量） |
| :---- | :---- | :---- | :---- |
| [百度AI同传][3] | 虚拟声卡来hook声音并进行同传，收费有点吓人|-|-|

# 离线翻译

| 厂家 | 说明 | - | - |
| :---- | :---- | :---- | :---- |
| [百度][4] | 技术服务费8万/年+8元/语种/台 |-|-|


```js

    let content = `
1
00:05:00,400 --> 00:05:15,300
This is an example of
a subtitle.

2
00:05:16,400 --> 00:05:25,300
This is an example of
a subtitle - 2nd subtitle.`;

    plugin.translate({
      lfrom:"en_US",
      lto:"zh_CN",
      content: content,
      success: function(res) {
        if(res.retcode == 0) {
          console.log("result", res.result)
        } else {
          console.warn("翻译失败", res)
        }
      },
      fail: function(res) {
        console.log("网络失败",res)
      }
    })
```

[1]: https://api.fanyi.baidu.com/product/113
[2]: https://api.fanyi.baidu.com/product/21
[3]: https://tongchuan.baidu.com/
[4]: http://api.fanyi.baidu.com/product/31
[5]: https://www.deepl.com/en/docs-api/
[6]: https://developers.weixin.qq.com/doc/offiaccount/Intelligent_Interface/AI_Open_API.html