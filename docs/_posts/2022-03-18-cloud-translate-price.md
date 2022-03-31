---
layout: post
title:  "20家机器翻译大比拼"
date:   2022-03-18 21:51:05 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---


# 文本翻译对比

| 厂家 | 免费额度 | 超出部分 | QPS（每秒访问量） |
| :---- | :---- | :---- | :---- |
| [谷歌][1] | 每月50万字 | $20/百万字符  | - |
| [百度翻译API][1] | 每月200万字 | 49元/百万字符  | 10 |
| [百度机器翻译][7] | 500万字符(终身) | 49元/百万字符 或 1000万/450  | 100 |
| [腾讯机翻][8] | 每月5百万字符 | 58元/百万字符  | 5(字符长度上限是2000字符) |
| [有道机翻][9] | 100元消费券(终身) | 48元/百万字符  | 5(字符长度上限是2000字符) |
| [阿里机翻][1] | 每月100万字 | 50元/百万字符  | 50(字符长度上限是5000字符) |
| [微软机翻][1] | 每月200万字 | -  | - |
| [讯飞机翻][10] | 200万字符(终身) | 2250元/25000万字符  | -(字符长度上限是5000字符)  |
| [华为机翻][11] | 每月100万字符 | 50元/百万字符  | -  |
| [IBM机翻][13] | 每月100万字符 | $0.02/THOUSAND CHAR  | -  |
| [京东机翻][12] | 免费试用500次 | 24元/百万字符  | -  |
| [Amazon机翻][12] | 每月200万字(首年) | $15/百万字符  | -  |
| [阿里文档翻译][1] | - | -  | - |
| [DeepL Free][5] | 每月50万字 |            -     | - |
| [微信翻译][6] | 提供英汉互翻，每次最大600Byte | -     | - |
| [微信同声传译][6]| 后台限制1000字节大小 | -     | - |

# 语音翻译

| 厂家 | 免费额度 | 超出部分 | QPS（每秒访问量） |
| :---- | :---- | :---- | :---- |
| [百度][2] | 每月可享1万次免费调用次数 | 0.025/次  | - |
| [百度翻译API][15] | - | 0.025/次  | -(无时间轴) |
| [微软语音翻译][17] | - | 0.025/次  | -(无时间轴) |


# 同传

| 厂家 | 免费额度 | 超出部分 | QPS（每秒访问量） |
| :---- | :---- | :---- | :---- |
| [百度AI同传][3] | 虚拟声卡来hook声音并进行同传，收费有点吓人|-|-|
| [有道实时语音翻译][9] | 996元/100小时 | -  | 5(字符长度上限是2000字符) |

# 离线翻译

| 厂家 | 说明 | - | - |
| :---- | :---- | :---- | :---- |
| [百度][4] | 技术服务费8万/年+8元/语种/台 |-|-|

[1]: https://api.fanyi.baidu.com/product/113
[2]: https://api.fanyi.baidu.com/product/21
[3]: https://tongchuan.baidu.com/
[4]: http://api.fanyi.baidu.com/product/31
[5]: https://www.deepl.com/en/docs-api/
[6]: https://developers.weixin.qq.com/doc/offiaccount/Intelligent_Interface/AI_Open_API.html
[7]: https://cloud.baidu.com/doc/MT/s/ykqq95r2y
[8]: https://cloud.tencent.com/document/product/551/35017
[9]: https://ai.youdao.com/product-fanyi-text.s
[10]: https://www.xfyun.cn/services/xftrans?target=price
[11]: https://www.huaweicloud.com/pricing.html?tab=detail#/nlp
[12]: https://neuhub.jd.com/market/api/471
[13]: https://cloud.ibm.com/catalog/services/language-translator
[14]: https://ai.youdao.com/streamingAudio.s
[15]: https://fanyi-api.baidu.com/doc/25
[16]: https://help.aliyun.com/product/54853.html?spm=5176.22414175.sslink.1.45693bddf1b5Bx
[17]: https://docs.microsoft.com/zh-cn/azure/cognitive-services/speech-service/get-started-speech-translation?tabs=script%2Cwindowsinstall
