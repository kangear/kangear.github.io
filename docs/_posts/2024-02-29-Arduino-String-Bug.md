---
layout: post
title:  "Arduino String陷阱"
date:   2024-02-29 14:25:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

Serial.println中看到“豆腐”其实是0x00，这个0x00在String和char array中会有截然相反的特性，前者正常打印，后者就完全无法作为字符串使用，因为会被识别为空，0x00是C字符串的结束。

```c
char zeroHello[] = {0x00, 'H', 'e', 'l', 'l', 'o'};

void setup() {
  Serial.begin(9600);
  String str = "";
  for (int i=0; i<sizeof(zeroHello); i++) {
    str += zeroHello[i];
  }
  Serial.println("zero hello str: ");
  Serial.println(str);

  Serial.println("zero hello char*: ");
  Serial.println((char*)zeroHello);
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

| ![有帮助的截图](/assets/微信图片_20240229143604.png) |
| :----------------------------------------: |
|          *运行结果截图*          |
