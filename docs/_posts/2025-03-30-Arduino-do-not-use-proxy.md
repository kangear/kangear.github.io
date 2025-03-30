---
layout: post
title:  "Arduino IDE不走代理？"
date:   2025-03-30 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---


这两天经历了奇怪的事情，就是`Arduino IDE`怎么配置都不走代理。我是在一个Windows 11的虚拟机中，刚开始直接系统级别配置成真机的代理地址，也把Arduino设置中的配置了，随后又直接安装了`Clash`都不行，最终强制使用`proxychains`，完整的命令如下：

```bash
./proxychains_win32_x64.exe -f proxychains.conf ../arduino-cli core install esp32:esp32@2.0.17
```

配置文件
```
[ProxyList]
socks5 192.168.1.177 7890
```

最终的配置是真机的代理地址，所以我觉得可能是新安装的Winddows虚拟机哪里没有配置好，导致一直不走代理。真机的代理还是没有问题的，但是直接在系统级设置也不走。`set`方式没有回头再设置，估计也能行。