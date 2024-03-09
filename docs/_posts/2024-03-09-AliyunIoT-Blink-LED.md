---
layout: post
title:  "阿里云物联网(飞燕)点灯"
date:   2024-03-09 16:40:00 +0800
categories: cloud
typora-copy-images-to: ../assets
typora-root-url: ../
---

关键字：`阿里云`、`物联网`、`飞燕`

# HelloWorld

开发板型号：Arudino D1

| ![有帮助的截图](/assets/微信截图_20240309173657.png) | ![有帮助的截图](/assets/微信截图_20240309173454.png) |
| :----------------------------------------: | :----------------------------------------: |
|          *板子图片*          |          *Hello World点灯*          |

# 配置Arduino并编译测试

安装库文件`ArduinoJson`、`PubSubClient`、`Crypto`。

```cpp
#include <ESP8266WiFi.h>
#include "AliyunIoTSDK.h"
#include <math.h>

static WiFiClient espClient;

// 产品和设备的信息
#define PRODUCT_KEY "a1XclUKKdSh"
#define DEVICE_NAME "qmni4YZDIur9dvtJo7cy"                                                   
#define DEVICE_SECRET "b0cc0b86d78a3a516d93976aa49d0afb"
#define REGION_ID "cn-shanghai"

// 设置WiFi
#define WIFI_SSID "QWRT-2.4G"
#define WIFI_PASSWD "youli2023"

void setup()
{
    Serial.begin(9600);//此处的波特率可以根据自己所需进行修改
    pinMode(LED_BUILTIN, OUTPUT);//定义I/O口

    // 初始化WiFi
    wifiInit(WIFI_SSID, WIFI_PASSWD);

    // 初始化iot，需传入WiFi的 client，和设备产品信息
    AliyunIoTSDK::begin(espClient, PRODUCT_KEY, DEVICE_NAME, DEVICE_SECRET, REGION_ID);

    // 绑定一个设备属性回调，当远程修改此属性，会触发 powerCallback
    // PowerSwitch 是在设备产品中定义的物联网模型的 id
    AliyunIoTSDK::bindData((char*)"powerstate", powerCallback);


}
// 初始化 wifi 连接
void wifiInit(const char *ssid, const char *passphrase)
{
    WiFi.mode(WIFI_STA);
    WiFi.begin(ssid, passphrase);
    while (WiFi.status() != WL_CONNECTED)
    {
        delay(1000);
        Serial.println("WiFi not Connect");
    }
    Serial.println("Connected to AP");
}
void loop()
{
    AliyunIoTSDK::loop();
    delay(1000);
}
void powerCallback(JsonVariant p)
{
    int PowerState = p["powerstate"];
    if (PowerState == 1)
    {
        digitalWrite(LED_BUILTIN, LOW);
    } else if(PowerState == 0){
        digitalWrite(LED_BUILTIN, HIGH);
    }
}
```
完整代码：

# 注册阿里云

## 注册
https://aliyun.com

## 打开 生活物联网平台（飞燕）
https://living.aliyun.com

# 添加项目
| ![有帮助的截图](/assets/微信截图_20240309174429.png) | ![有帮助的截图](/assets/微信截图_20240309174847.png) | ![有帮助的截图](/assets/微信截图_20240309175021.png) | ![有帮助的截图](/assets/微信截图_20240309175123.png) |
| :----------------------------------------: | :----------------------------------------: |:----------------------------------------: |:----------------------------------------: |
|          *1*          |         *2*          |         *3*          |         *4*          |

# 添加新设备

切换到【设备调试】，点击【新增加调试设备】，在对话框中直接点击【确定】，则会出现一个状态显示为【未激活】的设备，点击【查看】可以看到设备的三元组信息。
| ![有帮助的截图](/assets/微信截图_20240309175508.png) | ![有帮助的截图](/assets/微信截图_20240309175608.png) |
| :----------------------------------------: | :----------------------------------------: |
|          * 板子图片 *          |         * 板子图片 *          |


## 修改代码配置

将Arduino代码中的WiFi配置、设备三元信息配置。

## 在线

修改配置后，运行设备后会在线。

| ![有帮助的截图](/assets/微信截图_20240309184104.png) |
| :----------------------------------------: |
|          * 板子图片 *          |

# 添加到App进行测试

切换到【人机交互】。

## 设置【产品展示】和【设备面板】

| ![有帮助的截图](/assets/微信截图_20240309175216.png) |![有帮助的截图](/assets/微信截图_20240309175305.png) |![有帮助的截图](/assets/微信截图_20240309175339.png) |
| :----------------------------------------: |:----------------------------------------: |:----------------------------------------: |
|          *人机交互*          |         *产品展示*          |         *设备面板*          |


## 设置【产品说明书】

| ![有帮助的截图](/assets/微信截图_20240309175713.png) |
| :----------------------------------------: |
|          * 板子图片 *          |

## APP添加设备测试

| ![有帮助的截图](/assets/6229b47a03d15f2796b02b6bdbe3e69.jpg) | ![有帮助的截图](/assets/d314bfd2ef416ea4563d1323ab3d3da.jpg) | ![有帮助的截图](/assets/91a23e6cbd6571e6c52280614e20650.jpg) | ![有帮助的截图](/assets/aecb9fd7434ce893cc8dca90a002d7b.jpg) |
| :----------------------------------------: | :----------------------------------------: |:----------------------------------------: |:----------------------------------------: |
|          *APP主界面*          |          *添加设备*          |         *扫码添加成功*          |         *设备打开*          |

点击APP界面上的开关，Arduino D1上的LED会配合亮灭，以下是效果：
| ![有帮助的截图](/assets/ezgif-3-5baa397e49.gif) |
| :----------------------------------------: |
|          *运行效果图*          |


淘宝店：https://kangear.taobao.com/