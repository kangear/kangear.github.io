---
layout: post
title:  "HomeSpan 空调"
date:   2024-11-03 12:00:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

https://github.com/dingyiyi0226/homekit-air-conditioner
https://github.com/LouisLee985/Homekit_ESP_AC_IRemote

# 报错

| ![有帮助的截图](/assets/8e9edda86467f4cf7c488e59716a990.png) |
| :------------: | 
|          *报错*    | 


HomeSpan逼着把`ESP32库`升级，升级之后采用的是`IDF-5`，而`IRremoteESP8266`并未兼容`IDF-5`。

再次尝试把空调做出来，身边空调的遥控器背面型号为`YAP0F`，因为是型号是`格力`，很自然会打开一个`Gree`的例子来控制，结果控制无效。这次先使用`PulseViewer`来抓包，再结合[格力空调 YAPOF3 红外编码][1]以及[格力空调红外编码解析][2]，就决定改用`Kelvinator`的开空调Demo来测试，果然直接可以打开空调。

```
/* Copyright 2016, 2018 David Conran
*
* An IR LED circuit *MUST* be connected to the ESP8266 on a pin
* as specified by kIrLed below.
*
* TL;DR: The IR LED needs to be driven by a transistor for a good result.
*
* Suggested circuit:
*     https://github.com/crankyoldgit/IRremoteESP8266/wiki#ir-sending
*
* Common mistakes & tips:
*   * Don't just connect the IR LED directly to the pin, it won't
*     have enough current to drive the IR LED effectively.
*   * Make sure you have the IR LED polarity correct.
*     See: https://learn.sparkfun.com/tutorials/polarity/diode-and-led-polarity
*   * Typical digital camera/phones can be used to see if the IR LED is flashed.
*     Replace the IR LED with a normal LED if you don't have a digital camera
*     when debugging.
*   * Avoid using the following pins unless you really know what you are doing:
*     * Pin 0/D3: Can interfere with the boot/program mode & support circuits.
*     * Pin 1/TX/TXD0: Any serial transmissions from the ESP8266 will interfere.
*     * Pin 3/RX/RXD0: Any serial transmissions to the ESP8266 will interfere.
*   * ESP-01 modules are tricky. We suggest you use a module with more GPIOs
*     for your first time. e.g. ESP-12 etc.
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRsend.h>
#include <ir_Kelvinator.h>

const uint16_t kIrLed = 1;  // ESP8266 GPIO pin to use. Recommended: 4 (D2).
IRKelvinatorAC ac(kIrLed);  // Set the GPIO to be used for sending messages.

void printState() {
  // Display the settings.
  Serial.println("Kelvinator A/C remote is in the following state:");
  Serial.printf("  %s\n", ac.toString().c_str());
  // Display the encoded IR sequence.
  unsigned char* ir_code = ac.getRaw();
  Serial.print("IR Code: 0x");
  for (uint8_t i = 0; i < kKelvinatorStateLength; i++)
    Serial.printf("%02X", ir_code[i]);
  Serial.println();
}

void setup() {
  ac.begin();
  Serial.begin(115200);
  delay(200);

  // Set up what we want to send. See ir_Kelvinator.cpp for all the options.
  // Most things default to off.
  Serial.println("Default state of the remote.");
  printState();
  Serial.println("Setting desired state for A/C.");
  ac.on();
  ac.setFan(1);
  ac.setMode(kKelvinatorCool);
  ac.setTemp(26);
  ac.setSwingVertical(false, kKelvinatorSwingVOff);
  ac.setSwingHorizontal(true);
  ac.setXFan(true);
  ac.setIonFilter(false);
  ac.setLight(true);
}

void loop() {
  // Now send the IR signal.
#if SEND_KELVINATOR
  Serial.println("Sending IR command to A/C ...");
  ac.send();
#endif  // SEND_KELVINATOR
  printState();
  delay(5000);
}
```

那就可以把其和HomeSpan柔和在一起做出第一个空调控制器。


[1]: https://snowstar.org/2022/02/21/gree-yapof3-ir-format/
[2]: https://blog.csdn.net/weixin_44821644/article/details/108704768