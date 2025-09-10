---
layout: post
title:  "USB通断器(Matter版)使用说明"
date:   2025-09-03 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

# How it works

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/11bfd8f55b01f7c945972e960cd6b10c.mp4#t=0.001" type="video/mp4">
</video>

# Factory Reset

To reset the device to factory settings:

Press and hold the input button for about 5000 milliseconds. Then release the button to factory reset the device.
The device will then reboot and enter setup mode.

# Indicators

The device has the following indicators:
## Setup
- **Setup mode**: LED blinks continuously, about 4 seconds per cycle, with white color.
- **Setup started**: LED blinks continuously, about 1 second per cycle, with white color.
- **Setup complete**: LED shows the default state of the device and stops any ongoing patterns.
- **Setup failed**: LED shows the default state of the device and stops any ongoing patterns.
- **setup_mode_end**: LED shows the default state of the device and stops any ongoing patterns.
- **Device ready**: LED shows the default state of the device and stops any ongoing patterns.
## Functional
- **Factory reset triggered**: LED blinks continuously, about 0.4 seconds per cycle, with white color.
- **Forced rollback triggered**: LED blinks continuously, about 0.4 seconds per cycle, with white color.
- **Driver mode**: LED blinks continuously, about 1 second per cycle, with white color.
## Test Mode
- **Test mode start**: LED blinks for 1.5 seconds, about 0.5 seconds per cycle, with white color.
- **Test mode complete**: LED blinks for 3 seconds, about 0.5 seconds per cycle, with white color.
## Identification
- **Identification start**: LED blinks continuously, about 1 second per cycle, with white color.
- **Identification stop**: LED shows the default state of the device and stops any ongoing patterns.
- **Identification blink**: LED blinks for 1 second, about 1 second per cycle, with white color.
- **Identification breathe**: LED blinks for 15 seconds, about 1 second per cycle, with white color.
- **Identification okay**: LED blinks for 1.4 seconds, about 0.7 seconds per cycle, with white color.
- **Identification channel change**: LED blinks for 8 seconds, about 8 seconds per cycle, with white color.
- **Identification finish effect**: LED shows the default state of the device and stops any ongoing patterns.
- **Identification stop effect**: LED shows the default state of the device and stops any ongoing patterns.