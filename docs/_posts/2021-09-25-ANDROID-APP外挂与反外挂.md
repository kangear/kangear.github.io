---
layout: post
title:  "Android APP外挂与反外挂"
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
`APP方`很生气，居然可以这样。且听下回分解。从`android.os.ServiceManager#sCache`入手，通过反射将修改其值，可以达到**屏蔽**`屏幕元素节点`。
```java
public static void disableAccessibility() {
    if (!accessibilityDisabled) {
        accessibilityDisabled = true;
        try {
            Class cls = Class.forName("android.os.ServiceManager");
            if (cls != null) {
                Field declaredField = cls.getDeclaredField("sCache");
                if (declaredField != null) {
                    boolean isAccessible = declaredField.isAccessible();
                    declaredField.setAccessible(true);
                    Object obj = declaredField.get(null);
                    if (obj != null && (obj instanceof Map)) {
                        ((Map) obj).put("accessibility", new IBinder() {
                            public void dump(FileDescriptor fileDescriptor, String[] strArr) throws RemoteException {
                            }

                            public void dumpAsync(FileDescriptor fileDescriptor, String[] strArr) throws RemoteException {
                            }

                            public String getInterfaceDescriptor() throws RemoteException {
                                return null;
                            }

                            public boolean isBinderAlive() {
                                return true;
                            }

                            public void linkToDeath(DeathRecipient deathRecipient, int i) throws RemoteException {
                            }

                            public boolean pingBinder() {
                                return true;
                            }

                            public IInterface queryLocalInterface(String str) {
                                return null;
                            }

                            public boolean transact(int i, Parcel parcel, Parcel parcel2, int i2) throws RemoteException {
                                return true;
                            }

                            public boolean unlinkToDeath(DeathRecipient deathRecipient, int i) {
                                return true;
                            }
                        });
                        declaredField.setAccessible(isAccessible);
                    }
                }
            }
        } catch (Exception e) {
        }
    }
}
```
# 第三回合
## 攻
在第二回合，`App方`确实是防住了，又获取不了`屏幕元素节点`了。而`外挂方`又开始了新一轮的攻击。只要屏蔽其对`android.os.ServiceManager#sCache`通过反射进行的修改就可以了。制定出了A/B两个计划。A计划在`android.os.ServiceManager`中进行反制处理；B计划在`Field#setAccessible`进行反制。
先实现B计划：
```diff
project libcore/
diff --git a/ojluni/src/main/java/java/lang/reflect/Field.java b/ojluni/src/main/java/java/lang/reflect/Field.java
index a691766..c6fff50 100644
--- a/ojluni/src/main/java/java/lang/reflect/Field.java
+++ b/ojluni/src/main/java/java/lang/reflect/Field.java
@@ -641,6 +641,15 @@ class Field extends AccessibleObject implements Member {
     public native void setBoolean(Object obj, boolean z)
         throws IllegalArgumentException, IllegalAccessException;
+ 
+    @Override public void setAccessible(boolean flag) throws SecurityException {
+        if (!"java.util.HashMap<java.lang.String, android.os.IBinder>".equals(getGenericType().toString())) {
+            super.setAccessible(flag);
+        }
+    }
+
+
+
```
三行代码搞定，想必这次又能将`APP方`气得吐血。

## 防
这。。。  
待我归来。

[1]: https://developer.android.com/reference/android/accessibilityservice/AccessibilityService