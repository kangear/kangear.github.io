---
layout: post
title:  "Arduino中数组太长导致重启"
date:   2024-02-25 22:30:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

```c
void heartbeat() {
  char send_buffer[] = {0x18, 0x30, 0x02, 0x00, 0x00, 0x00, 0x18, 0x9D};
  char read_buf[1024] = {0};
  int len = 0;
  sendHex(send_buffer, sizeof(send_buffer) / sizeof(send_buffer[0]), read_buf, 1024, &len, 1000);

  parseBuf(read_buf, len);
}
```

将1024改为256就好了，这是在上操作系统中不常见的问题。