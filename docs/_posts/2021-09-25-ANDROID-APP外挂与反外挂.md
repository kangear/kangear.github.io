---
layout: post
title:  "ANDROID APP外挂与反外挂"
date:   2021-09-25 22:44:05 +0800
categories: jekyll update
typora-copy-images-to: ../asserts
typora-root-url: ../
---

# 前言

以Android为例，外挂一般是基于Android系统为辅助系统（洋文[AccessibilityService][1]）开发。辅助系统是Android为视力障碍人士提供的API接口，方便一些公司为视力障碍人士开发专门针对手机系统使用的一些服务，比如可以自动阅读微信文字，自动在美团购外卖，或者是在滴滴上打车。然而这个接口却被广泛用于外挂中，比如自动抢微信红包。  
下面以武侠小说的方式来说明，「外挂方」攻，「App方」防。

# 第一回合
## 攻
如果`App方`不作任何防范，`外挂方`是可以抓取到`界面元素节点`做一些自动化操作。`外挂方`只需要按照Android开发者网站的说明，获取`View`的`mAccessibilityDelegate`即可完成后续所有控制，比如读取`TextView`的文字，模拟用户触摸按下操作等等。

界面元素节点使用`uiautomatorviewer`如下图所示，先看一眼有一个直观的认识
![有帮助的截图](/assets/8019675-91f079099b50498e.webp)

左侧是手机界面，右侧是元素节点，已经可以获取到界面中的文字，每个元素的位置。

## 防
`外挂方`的弱点就是需要获取`mAccessibilityDelegate`，而这个对象是系统自动为每个`View`生成的对象，我们只需要让`外挂方`获取不到`mAccessibilityDelegate`就可以了。非常好，系统有这么一个接口`View#setAccessibilityDelegate`，我们只需在`BaseActivity`中要调用如下方法，就可以生成一个无效的对象，这个对象不能获取任何`界面元素节点`，也就无法完成模拟用户触摸点击等操作。
```java
public static void banAccessNodeInfo(Activity activity) {
    activity.getWindow().getDecorView()
        .setAccessibilityDelegate(new View.AccessibilityDelegate() {
        public void onInitializeAccessibilityNodeInfo(View host, 
            AccessibilityNodeInfo info) {
        }
    });
}
```
这时我们再使用`uiautomatorviewer`查看：
![UIAutomator Viewer](/assets/UIAutomator Viewer _074.jpg)
可以看到左侧将无法定位任何元素，获取到的是一个0大小的View。

# 第二回合
## 攻
经过上个回合，我们得知了`App方`是调用`setAccessibilityDelegate`。那么我们改系统不允许他调用。
```diff
diff --git a/core/java/android/view/View.java b/core/java/android/view/View.java
index 166d6b7..d2692d2 100644
--- a/core/java/android/view/View.java
+++ b/core/java/android/view/View.java
@@ -8484,6 +8484,24 @@ public class View implements Drawable.Callback, KeyEvent.Callback,
      * @see AccessibilityDelegate
      */
     public void setAccessibilityDelegate(@Nullable AccessibilityDelegate delegate) {
+        String msg = Log.getStackTraceString(new Throwable());
+        boolean needCatch = msg.contains("banAccessNodeInfo")
+        if (needCatch)
+            return;
         mAccessibilityDelegate = delegate;
     }
```
经过如此改造，`外挂方`又可以获取真实的`界面元素节点`。并进行外挂了。

## 防
`APP方`很生气，居然可以这样。且听下回分解。


[1]: https://developer.android.com/reference/android/accessibilityservice/AccessibilityService