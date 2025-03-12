---
layout: post
title:  "ESP32 BLE for Arduino"
date:   2025-03-12 23:00:00 +0800
categories: ic
typora-copy-images-to: ../assets
typora-root-url: ../
---

准备基于`BK3432`写一个基于Beacon广播方式的遥控接收器，但是资料太少，也几乎没有开源参与，联系了原厂得到答复不直接对客户，又联系了代理，购买了开发板和烧录器，代码的例子又特别少，痛苦的我拿起电烙铁焊接了一会电路板来平静糟糕的心情，果然灵感来袭，我完全可以先使用ESP32来实现，这样至少可以先了解这个方案的可行性。

## BLE库

像BK3432属于资料太少，而像ESP32又太多，在原厂主动支持Arduino之前网上有了一些第三方的支持，比如[nkolban/ESP32_BLE_Arduino][1]、[peterk54/ESP32BLESimpleAdvertiser][2]。

目前官方的库已开发位于：[https://github.com/espressif/arduino-esp32/tree/master/libraries/BLE][3]

例子相当充分，可以直接拿来实现自己的idea

| ![alt text](/assets/espressif_arduino-esp32_libraries_BLE_examples.png) |
| :------------: | 
|   1    |


```cpp
/*
   Based on Neil Kolban example for IDF: https://github.com/nkolban/esp32-snippets/blob/master/cpp_utils/tests/BLE%20Tests/SampleScan.cpp
   Ported to Arduino ESP32 by Evandro Copercini
   Changed to a beacon scanner to report iBeacon, EddystoneURL and EddystoneTLM beacons by beegee-tokyo
   Upgraded Eddystone part by Tomas Pilny on Feb 20, 2023
*/

#include <Arduino.h>

#include <BLEDevice.h>
#include <BLEUtils.h>
#include <BLEScan.h>
#include <BLEAdvertisedDevice.h>
#include <BLEEddystoneURL.h>
#include <BLEEddystoneTLM.h>
#include <BLEBeacon.h>

int scanTime = 5;  //In seconds
BLEScan *pBLEScan;

class MyAdvertisedDeviceCallbacks : public BLEAdvertisedDeviceCallbacks {
  void onResult(BLEAdvertisedDevice advertisedDevice) {
    if (advertisedDevice.haveName()) {
      Serial.print("Device name: ");
      Serial.println(advertisedDevice.getName().c_str());
      Serial.println("");
    }

    if (advertisedDevice.haveServiceUUID()) {
      BLEUUID devUUID = advertisedDevice.getServiceUUID();
      Serial.print("Found ServiceUUID: ");
      Serial.println(devUUID.toString().c_str());
      Serial.println("");
    }

    if (advertisedDevice.haveManufacturerData() == true) {
      String strManufacturerData = advertisedDevice.getManufacturerData();

      uint8_t cManufacturerData[100];
      memcpy(cManufacturerData, strManufacturerData.c_str(), strManufacturerData.length());

      if (strManufacturerData.length() == 25 && cManufacturerData[0] == 0x4C && cManufacturerData[1] == 0x00) {
        Serial.println("Found an iBeacon!");
        BLEBeacon oBeacon = BLEBeacon();
        oBeacon.setData(strManufacturerData);
        Serial.printf("iBeacon Frame\n");
        Serial.printf(
          "ID: %04X Major: %d Minor: %d UUID: %s Power: %d\n", oBeacon.getManufacturerId(), ENDIAN_CHANGE_U16(oBeacon.getMajor()),
          ENDIAN_CHANGE_U16(oBeacon.getMinor()), oBeacon.getProximityUUID().toString().c_str(), oBeacon.getSignalPower()
        );
      } else {
        Serial.println("Found another manufacturers beacon!");
        Serial.printf("strManufacturerData: %d ", strManufacturerData.length());
        for (int i = 0; i < strManufacturerData.length(); i++) {
          Serial.printf("[%X]", cManufacturerData[i]);
        }
        Serial.printf("\n");
      }
    }

    if (advertisedDevice.getFrameType() == BLE_EDDYSTONE_URL_FRAME) {
      Serial.println("Found an EddystoneURL beacon!");
      BLEEddystoneURL EddystoneURL = BLEEddystoneURL(&advertisedDevice);
      Serial.printf("URL bytes: 0x");
      String url = EddystoneURL.getURL();
      for (auto byte : url) {
        Serial.printf("%02X", byte);
      }
      Serial.printf("\n");
      Serial.printf("Decoded URL: %s\n", EddystoneURL.getDecodedURL().c_str());
      Serial.printf("EddystoneURL.getDecodedURL(): %s\n", EddystoneURL.getDecodedURL().c_str());
      Serial.printf("TX power %d (Raw 0x%02X)\n", EddystoneURL.getPower(), EddystoneURL.getPower());
      Serial.println("\n");
    }

    if (advertisedDevice.getFrameType() == BLE_EDDYSTONE_TLM_FRAME) {
      Serial.println("Found an EddystoneTLM beacon!");
      BLEEddystoneTLM EddystoneTLM(&advertisedDevice);
      Serial.printf("Reported battery voltage: %dmV\n", EddystoneTLM.getVolt());
      Serial.printf("Reported temperature: %.2f°C (raw data=0x%04X)\n", EddystoneTLM.getTemp(), EddystoneTLM.getRawTemp());
      Serial.printf("Reported advertise count: %lu\n", EddystoneTLM.getCount());
      Serial.printf("Reported time since last reboot: %lus\n", EddystoneTLM.getTime());
      Serial.println("\n");
      Serial.print(EddystoneTLM.toString().c_str());
      Serial.println("\n");
    }
  }
};

void setup() {
  Serial.begin(115200);
  Serial.println("Scanning...");

  BLEDevice::init("");
  pBLEScan = BLEDevice::getScan();  //create new scan
  pBLEScan->setAdvertisedDeviceCallbacks(new MyAdvertisedDeviceCallbacks());
  pBLEScan->setActiveScan(true);  //active scan uses more power, but get results faster
  pBLEScan->setInterval(100);
  pBLEScan->setWindow(99);  // less or equal setInterval value
}

void loop() {
  // put your main code here, to run repeatedly:
  BLEScanResults *foundDevices = pBLEScan->start(scanTime, false);
  Serial.print("Devices found: ");
  Serial.println(foundDevices->getCount());
  Serial.println("Scan done!");
  pBLEScan->clearResults();  // delete results fromBLEScan buffer to release memory
  delay(2000);
}
```

[1]: https://github.com/nkolban/ESP32_BLE_Arduino?tab=readme-ov-file
[2]: https://github.com/peterk54/ESP32BLESimpleAdvertiser
[3]: https://github.com/espressif/arduino-esp32/tree/master/libraries/BLE



