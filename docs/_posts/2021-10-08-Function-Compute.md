---
layout: post
title:  "阿里云函数计算踩坑记录"
date:   2021-10-08 18:00:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

函数计算，以下简称fc。是阿里推出的一种新的开发云服务的方式，相比ECS方式能达到像官网上吹的那样可以Serverless，但是这其中也有很多坑。由于笔者采用的nodejs开发，以下就以nodejs为例。

# 轻量级
直接在fc控制台就可以开始一个helloword，不需要任何本地工程，也不需要了解`fun nas vpc 自定义域名 https`等等这些名词。这个我这里就不多介绍了，我说说这种方式的弊端：
```
1. 有容量限制，如果代码和依赖的大小大于50M就需要提工单申请，目前最大也只能申请100M。而你稍微添加个依赖就有可能大于100M。
2. 如果你要上传文件，fc是有6M的最大要求的，如果文件大于6M是不支持的；
```
**注**：但是也需要了解一大票名词"服务 函数 触发器 版本 别名"等等。它们之间的关系我是理解透了，但是我画不出来它们的关系图给大家看，推荐先玩「轻量级」的，把这些词和关系理解清楚。



# 高级Pro版
玩过了轻量级，你可能想如何“做大”，轻量级只能是玩票。如果就玩大的，比较完全代替ECS，需要把之前的需求全部在fc平台上解决，比如解决访问数据库，如何访问oss，如何调用本地命令。后续我一个一个讲解。

玩Pro版需要接触到`fun nas vpc docker`等等这些词。不过也可以先只接触`fun`，这是一个工具，能做一些自动化操作。能把本地工程直接同步到fc云端。

```bash
# 安装docker
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun

# 安装fun（目前使用npm命令安装的fun工具比较老，最后加入群要一个最新的）
sudo npm install @alicloud/fun -g

# 其他启动
sudo fun local start fc.abc.com
# 上传
sudo fun nas sync
sudo fun deploy 

```

# 区分内测正式版
采用【版本】方式。自定义域名时没有办法靠PATH来区分了，比如abc.com/latest为内测 abc.com/为正式，因为我nodejs采用了express框架，这会和这内部的冲突，只能fc.abc.com 正式（${版本号}），fc2.abc.com 内测（LATEST）。

# 如何保存请求body和响应body
在使用传统ECS的时候，上面布了nginx，使用nginx插件可以记录每次请求的body和响应的body以做后续的debug。如果在函数计算上应该如何实现这个功能呢？
> 函数计算不会记录用户 request 和 response 的内容的，需要您在函数中打日志记录

# 如何调用Linux命令
我在传统的ECS上如果要调用系统命令比如ffmpeg，只需要`sudo apt-get install ffmpeg`，然后调用 shell的方式进行调用该命令。在函数计算环境如何安装ffmpeg，如何调用呢？
> (等待答复)

# 日志
日志服务；
1）非LATEST版本如何启动日志服务，日志服务如何优化。

# FC访问数据库RDS
由于fc不像ecs有固定ip，所以fc对数据库rds的访问只能通过外网IP(0.0.0.0/0段白名单)或者vpc内网(具体vpc内网段白名单)来访问，调试阶段可以采用前者方式比较方便。发布时为了数据安全要将rds由经典网络切成专用网络VPC，将vpc内网ip添加成rds的访问白名单中；将本地机器的外网IP也添加到访问白名单中；将之前设置的(0.0.0.0/0段白名单)移除。程序代码中使用env.local来动态配置内外网域名。nodejs例子如下：
```
host: process.env.local ? 'waiwang.mysql.rds.aliyuncs.com' : 'neiwang.mysql.rds.aliyuncs.com', 
```
这样可以同一套代码，本地使用运行的时候采用外网访问数据库，发布到函数计算上时采用内网来访问数据库。
这样就保证的安全性和便利性。

# FC访问OSS
无需要额外配置，可以直接使用`multer`访问。

# 第一次访问是为慢
为什么第一次访问是为慢，连续访问就正常了。这是为什么呢?
具体描述：
函数计算如果几小时不访问（GET），再访问（GET）的时候第一次时间比较长，需要10秒左右才能请求成功（GET）。然后再接着访问就能和移植前的ECS一样很快了。从上周移植完成一直能测试出这个问题。这里面的原理是什么呢？为什么会需要请求这么长时间。
> 冷启动导致，一会无访问就会不关闭了。再访问时才会重新冷启动。要解决这个问题可以使用「预留资源」，或者再创建一个函数每3分钟访问一下，保证不释放。
https://help.aliyun.com/document_detail/138103.html?spm=a2c4g.11186623.6.630.5157265aVWBVvX

评价：函数计算的缺点要

# 高级选项
## webpack打包
使用webpack打包可以将一百兆的项目，打包压缩下来也就一两兆。如何使用呢？

## 改变上传文件的方式
https://help.aliyun.com/document_detail/31920.html?spm=a2c4g.11186623.6.1528.28287a46zkoQ05

# 使用fun工具后会有多余的服务
fun工具自动化创建nas/vps等也是使用函数计算功能实现的，特别是在你配置`NasConfig: Auto`的时候。但是创建完成之后没有将本地的配置自动修改，没有将函数计算上的临时服务删除。

# 如何再创建一个非http的函数
可以不使用custom环境

# 函数计算中的「cdn加速」和「预留资源」关系
如果不预留资源，访问的时候会有「冷启动」的问题。问题来了，cdn加速是将代码分布的全国各省服务器，「预留资源」能解决包含「cdn加速」的所有「冷启动」问题吗？

# http触发器 添加认证方法
云端代码不需要作任何变动，只需要在客户端做即可。
https://help.aliyun.com/document_detail/148553.html?spm=a2c4g.11186623.6.773.130d5da7WwN6U8
```
implementation 'com.aliyun:aliyun-java-sdk-fc:1.8.1'
```

# 收费
```
ECS :包年包月，没有其他费用
函数计算:
费用:
 调用次数: 1.33元/百万次
 计算力cu:计费方式略复杂
 公网流量: 1G/0.8元

 预留资源(计算力cu) : 1个/80/月 和按量资源收费一样的
免费额度:
 调用次数:每月前100万次函数调用免费。
 执行时间:每月前400000 (cu-秒)费用免费。
```

# 注意事项
1. 本地使用`sudo fun local start fc.abc.com`会有一些问题，一个本地函数不会调用；
2. 上传文件只能小于6M；如果大于6M。需要改成oss直传方式；



# xxx
```
The CA process either cannot be started or exited:ContainerStartDuration:25909615437. CA process cannot be started or exited already: rpc error: code = 106 desc = ContainerStartDuration:25000000000. Ping CA failed due to: dial tcp 21.0.7.1:9000: i/o timeout Logs : 2020-04-16T11:33:08.264632290Z internal/modules/cjs/loader.js:638
2020-04-16T11:33:08.264671945Z     throw err;
2020-04-16T11:33:08.264677460Z     ^
2020-04-16T11:33:08.264681566Z 
2020-04-16T11:33:08.264691387Z Error: Cannot find module './$data'
2020-04-16T11:33:08.264696153Z     at Function.Module._resolveFilename (internal/modules/cjs/loader.js:636:15)
2020-04-16T11:33:08.264701120Z     at Function.Module._load (internal/modules/cjs/loader.js:562:25)
2020-04-16T11:33:08.264705735Z     at Module.require (internal/modules/cjs/loader.js:692:17)
2020-04-16T11:33:08.264709425Z     at require (internal/modules/cjs/helpers.js:25:18)
2020-04-16T11:33:08.264713278Z     at Object.\u003canonymous\u003e (/mnt/auto/node_modules/ajv/lib/ajv.js:10:23)
2020-04-16T11:33:08.264717362Z     at Module._compile (internal/modules/cjs/loader.js:778:30)
2020-04-16T11:33:08.264721103Z     at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
2020-04-16T11:33:08.264724953Z     at Module.load (internal/modules/cjs/loader.js:653:32)
2020-04-16T11:33:08.264728844Z     at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
2020-04-16T11:33:08.264733118Z     at Function.Module._load (internal/modules/cjs/loader.js:585:3)
```

# 预留实例计费
按量计费的: 每小时费用：60*60*0.00011108=0.4 一个月228左右
包年包月: 80一个月左右
使用「预留实例」时要注意。

# 错误：ENOSPC: System limit for number of file watchers reached, watch '/tmp/node-watch-472d3e1c60fc8'
这是由于监听文件大于系统最高限制了，需要执行如下命令把限制放宽一些
```
sudo sysctl fs.inotify.max_user_watches=524288
```

# 长链接ws
fc是不支持长链接的，比如ws。所以fc对还差很多。


# 错误：xxx
耗时请求前端超时后断开连接导致。前端设置超时时间长一些，fc性能不及ECS，相同请求在fc下就会慢一些。

写于2021年6月
