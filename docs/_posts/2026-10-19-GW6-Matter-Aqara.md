---
layout: post
title:  "Matter 网关GW6使用说明"
date:   2026-10-19 10:00:00 +0800
categories: a
typora-copy-images-to: ../assets
typora-root-url: ../
---

## 1. 开始之前

FPOON GW6伴侣网关（Matter版本）同时支持多款设备接入到HomeKit、Aqara、Google Home、Alexa等，自发电门铃、自发电随意贴、摆臂机器人、跷跷板机器人、手指机器人、触摸机器人。

| [<img src="/assets/3ac50f265208aad5c544680dc9dac8fa.png" width="800"/>](/assets/3ac50f265208aad5c544680dc9dac8fa.png)|
| :------------: | 
|          原理    |


## 2 Aqara App添加

插电后指示灯会闪，扫码添加，然后按照以下方式进入管理界面

<table style="table-layout: fixed; width: 100%; border-collapse: collapse;" border="1">
  <tr>
    <td style="text-align: center;">
      <img src="/assets/20261019171813_372_6.jpg" alt="图1" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/20261019171813_373_6.jpg" alt="图2" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/20261019171813_374_6.jpg" alt="图3" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/20261019171813_375_6.jpg" alt="图4" style="width: 100%;" />
    </td>
    <td style="text-align: center;">
      <img src="/assets/842f7565905401e4d8edf707d8679b53.jpg" alt="图5" style="width: 100%;" />
    </td>
  </tr>
  <tr>
    <td style="text-align: center;">Aqara App 按下右上角三个点</td>
    <td style="text-align: center;">按下 Network Information</td>
    <td style="text-align: center;">找到IP Address并复制</td>
    <td style="text-align: center;">在Safari中打开</td>
    <td style="text-align: center;">右上角+号添加子设备</td>
  </tr>
</table>



<div style="display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 16px;">
  <div>
    <a href="/a/2025/03/21/HomeKit-Finger-Bot2.html" style="display: flex; flex-direction: column; aspect-ratio: 1; box-sizing: border-box; align-items: center; justify-content: center; gap: 2px; padding: 4% 8%; border-radius: 22%; background: #f5f5f7; color: inherit; text-decoration: none;">
      <img src="/assets/ScreenShot_2026-10-12_152603_332.png" alt="手指机器人" style="width: 100%; flex: 1; min-height: 0; object-fit: contain;" />
      <span style="width: 100%; font-size: clamp(12px, 3.5vw, 14px); line-height: 1.2; text-align: center; white-space: nowrap;">手指机器人</span>
    </a>
  </div>
  <div>
    <a href="/a/2025/04/03/HomeKit-Finger-Bot-TouchScreen.html" style="display: flex; flex-direction: column; aspect-ratio: 1; box-sizing: border-box; align-items: center; justify-content: center; gap: 2px; padding: 4% 8%; border-radius: 22%; background: #f5f5f7; color: inherit; text-decoration: none;">
      <img src="/assets/微信截图_20250403202935.png" alt="触控机器人" style="width: 100%; flex: 1; min-height: 0; object-fit: contain;" />
      <span style="width: 100%; font-size: clamp(12px, 3.5vw, 14px); line-height: 1.2; text-align: center; white-space: nowrap;">触控机器人</span>
    </a>
  </div>
  <div>
    <a href="/a/2025/04/06/HomeKit-Switch-Mate.html" style="display: flex; flex-direction: column; aspect-ratio: 1; box-sizing: border-box; align-items: center; justify-content: center; gap: 2px; padding: 4% 8%; border-radius: 22%; background: #f5f5f7; color: inherit; text-decoration: none;">
      <img src="/assets/ScreenShot_2026-10-12_153212_154.png" alt="摆臂机器人" style="width: 100%; flex: 1; min-height: 0; object-fit: contain;" />
      <span style="width: 100%; font-size: clamp(12px, 3.5vw, 14px); line-height: 1.2; text-align: center; white-space: nowrap;">摆臂机器人</span>
    </a>
  </div>
  <div>
    <a href="/a/2026/03/21/HomeKit-Switch-Mate2.html" style="display: flex; flex-direction: column; aspect-ratio: 1; box-sizing: border-box; align-items: center; justify-content: center; gap: 2px; padding: 4% 8%; border-radius: 22%; background: #f5f5f7; color: inherit; text-decoration: none;">
      <img src="/assets/ScreenShot_2026-10-12_153355_834.png" alt="跷跷板机器人" style="width: 100%; flex: 1; min-height: 0; object-fit: contain;" />
      <span style="width: 100%; font-size: clamp(12px, 3.5vw, 14px); line-height: 1.2; text-align: center; white-space: nowrap;">跷跷板机器人</span>
    </a>
  </div>
  <div>
    <a href="/a/2025/03/06/HomeKit-Doorbell.html" style="display: flex; flex-direction: column; aspect-ratio: 1; box-sizing: border-box; align-items: center; justify-content: center; gap: 2px; padding: 4% 8%; border-radius: 22%; background: #f5f5f7; color: inherit; text-decoration: none;">
      <img src="/assets/ScreenShot_2026-01-29_131152_030.png" alt="自发电门铃" style="width: 100%; flex: 1; min-height: 0; object-fit: contain;" />
      <span style="width: 100%; font-size: clamp(12px, 3.5vw, 14px); line-height: 1.2; text-align: center; white-space: nowrap;">自发电门铃</span>
    </a>
  </div>
  <div>
    <a href="/a/2025/04/28/HomeKit-Wireless-Switch.html" style="display: flex; flex-direction: column; aspect-ratio: 1; box-sizing: border-box; align-items: center; justify-content: center; gap: 2px; padding: 4% 8%; border-radius: 22%; background: #f5f5f7; color: inherit; text-decoration: none;">
      <img src="/assets/ScreenShot_2026-10-12_153509_861.png" alt="自发电随意贴" style="width: 100%; flex: 1; min-height: 0; object-fit: contain;" />
      <span style="width: 100%; font-size: clamp(12px, 3.5vw, 14px); line-height: 1.2; text-align: center; white-space: nowrap;">自发电随意贴</span>
    </a>
  </div>
</div>


## 4. 恢复出厂

设备上的按钮`长按10秒钟`指示灯由闪烁到熄灭，即可恢复出厂。

<video width="240" height="320" controls>
  <source src="https://homekit.oss-cn-beijing.aliyuncs.com/b98a5f7368f729e9e6152d88bc56bb44.mp4#t=0.001" type="video/mp4">
</video>

[2]: /cloud/2024/11/15/HomeSpan-Light-Readme.html