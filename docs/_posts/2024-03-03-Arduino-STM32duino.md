---
layout: post
title:  "Arduino STM32druino"
date:   2024-03-03 17:50:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

关键字：`Arduino`、`Nucleo-64`、`STM32F103RB`

| ![有帮助的截图](/assets/微信截图_20240303180614.png) |
| :-----------------: |
|         *板子图片*   |

| ![有帮助的截图](/assets/微信截图_20240303180322.png) | ![有帮助的截图](/assets/f8f6729114de691f89afd2013304bb0.jpg) | ![有帮助的截图](/assets/copy_D9B317BD-A603-4EE6-A66A-0DECE927984E-min.gif) |
| :-----------: | :---------------: | :----------: |
|    *HelloWorld点灯*  |  *注意配置-F103RB*   |   *显示效果*   |

默认调试串口是STLink虚拟的，使用串口助手连接“默认的D1D0”是接收到不数据的，因为那是Serial2。

| ![有帮助的截图](/assets/微信截图_20240304154255.png) | ![有帮助的截图](/assets/a3df58f1215c6eaea614d2800021e28.png) |
| :----------------------------------------: | :----------------------------------------: |
|          *串口Demo*          |          *串口名字*          |


# PINOUT

| ![有帮助的截图](/assets/FT4S7MBJ98RBEZI.jpg) | ![有帮助的截图](/assets/F8VOF5RJ98RBEZH.png) |
| :----------------------------------------: | :----------------------------------------: |
|          *Arduino风格管脚*          |          *外围引脚*          |

补充配置电路板
```
https://github.com/stm32duino/BoardManagerFiles/raw/main/package_stmicroelectronics_index.json
```

更多参考资料：
https://os.mbed.com/platforms/ST-Nucleo-F103RB/


```
For STM32F103C8T6 board, the default Serial is actually mapped to the 2nd serial port of the chip. This port is wired to the on-board ST-link. You can then plug your PC to the USB-port of the ST-link and get Serial Monitor on Arduino IDE right away.
```
来自：https://www.stm32duino.com/viewtopic.php?t=1354

串口1

| ![有帮助的截图](/assets/微信截图_20240320221106.png) |
| :----------------------------------------: |
|          *Serial1的使用*          |

```cpp
/* 
HardwareSerial Serial1(PA10, PA9);

// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
  Serial.begin(115200);
  // Serial1.begin(115200);
  Serial1.begin(115200);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(LED_BUILTIN, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
  Serial.println("Hello World! Here is Serial");
  // Serial1.println("Hello World! Here is Serial1");
  Serial1.println("Hello World! Here is Serial1");
}
```

# 资源配置

默认D0、D1不可用，需要按照如下图所示：

| ![有帮助的截图](/assets/4fd8daead63fd88975c348e112e1bc0.jpg) |
| :----------------------------------------: |
|          *修复D0 D1不可用问题*          |

