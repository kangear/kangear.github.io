---
layout: post
title:  "Arduino Switch语句中要加{}"
date:   2024-02-28 13:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

众所周知，在Switch语句中不能声明和定时变量，但是Arduino的编译器不能识别到这一点，如果IDLE的case没有被{}包起来，则这个switch会产生奇怪的特性，也就是进不到START这个case，这个问题耗费了的几个小时的时间，这里下下来警示后人。

所以养成习惯，switch的case默认被{}包起来。

```c
// 状态机 1.start 2.runnig 3. stop
enum STATE {
    IDLE, START, RUNNING, STOP  };
volatile int mState = IDLE;

bool init_at() {
    return true;
}

void setup() {
  Serial.begin(9600);
}

void loop() {
  Serial.println("loop...");
  Serial.println(mState, DEC);
  delay(1000);
  switch (mState) {
    case IDLE: 
    // {
      Serial.println("STATE_IDLE times: ");
      bool ret = init_at();
      if (ret) {
        mState = START;
      }
      break;
    // }
    case START: {
      Serial.println("STATE_START times: ");
      break;
    }
    default:
      Serial.println("mState default times: ");
      break;
  }
  Serial.println("loop2...");
}
```

| ![有帮助的截图](/assets/微信截图_20240228135047.png) |
| :----------------------------------------: |
|          *运行结果截图*          |
