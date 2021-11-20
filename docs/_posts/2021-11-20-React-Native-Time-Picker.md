---
layout: post
title:  "react-native-date-picker报错：int无法转换为String"
date:   2021-11-20 16:17:05 +0800
categories: android
typora-copy-images-to: ../assets
typora-root-url: ../
---

一定正常使用是RN的Android工程，clone到另外一台电脑上，`yarn`下载依赖就编译不过去了，报如下错误：

```
node_modules/react-native-date-picker/android/src/main/java/com/henninghall/date_picker/pickers/AndroidNative.java:57: 错误: 不兼容的类型: int无法转换为String
            setTextColor(color);
```

Package.json中的配置如下：
```
"react-native-date-picker": "^3.3.1"
```

搜索到仓库主页如下：

| ![有帮助的截图](/assets/1637395269910.jpg) |
| :----------------------------------------: |
|          *版本历史*          |


根据经验推测是开发者推了最新版，但是兼容不好，需要强制为当前版本，根据[这里][1]的package.json的使用说明如下：

| ![有帮助的截图](/assets/WX20211120-160350.png) |
|:--:|
| Package.json说明 |

那么答案就有了:

```diff
diff --git a/package.json b/package.json
index 4141cb3..c005c87 100644
--- a/package.json
+++ b/package.json
@@ -39,7 +39,7 @@
     "react-native-tcp-socket": "^5.2.0",
     "react-native-vector-icons": "^8.1.0",
     "teaset-pro": "^0.8.4",
-    "react-native-date-picker": "^3.3.1"
+    "react-native-date-picker": "3.3.1"
   },
   "devDependencies": {
     "@babel/core": "^7.8.4"
```


[1]: https://stackoverflow.com/questions/22343224/whats-the-difference-between-tilde-and-caret-in-package-json
