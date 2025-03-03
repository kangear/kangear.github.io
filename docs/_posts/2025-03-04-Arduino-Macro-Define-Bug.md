---
layout: post
title:  "Arduino #define 宏定义陷阱"
date:   2025-03-04 00:25:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

```c
#define MODEL A

#if MODEL == A

#error "error A"
#define PROTOCAL 13

#elif MODEL == B

#error "error B"
#define PROTOCAL 14

#endif
```

这样不会报错，但是其实逻辑不对，两个`#error`都不会触发。需要在头部定义A和B才能正常。
```c
#define A 1
#define B 2
```

