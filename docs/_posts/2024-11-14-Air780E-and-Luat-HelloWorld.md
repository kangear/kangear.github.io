---
layout: post
title:  "基于Air780E和Luat的HelloWorld"
date:   2024-11-14 16:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

# 运行效果

| ![有帮助的截图](/assets/微信截图_20241114164202.png) |
| :------------: | 
|          *运行效果*    | 

# 下载工具和固件

固件：https://gitee.com/openLuat/LuatOS/releases   
比如：core_V1112.zip

首先下载最新版本的Luatools：[点我下载][1]

| ![有帮助的截图](/assets/微信截图_20241114165224.png) |
| :------------: | 
|          *编译并烧录代码*    | 


# 源码

```lua

-- LuaTools需要PROJECT和VERSION这两个信息
PROJECT = "helloworld"
VERSION = "1.0.0"

-- 引入必要的库文件(lua编写), 内部库不需要require
sys = require("sys")

log.info("main", "hello world")

print(_VERSION)

sys.timerLoopStart(function()
    print("hi, LuatOS")
    print("mem.lua", rtos.meminfo())
    print("mem.sys", rtos.meminfo("sys"))
end, 3000)


-- 用户代码已结束---------------------------------------------
-- 结尾总是这一句
sys.run()
-- sys.run()之后后面不要加任何语句!!!!!
```

代码来源：https://gitee.com/openLuat/LuatOS-Air780E/blob/master/demo/hello_world/main.lua

[1]: https://luatos.com/luatools/download/last