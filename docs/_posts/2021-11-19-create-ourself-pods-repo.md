---
layout: post
title:  "iOS第一课：解决SwiftChart不兼容最新版Swift问题"
date:   2021-11-19 14:43:05 +0800
categories: iOS
typora-copy-images-to: ../asserts
typora-root-url: ../
---

`SwiftChart`这个依赖在最新版本的Xcode和Swift语言中编译会报错，但是看上游短时间内也没有想要解决的意思。这里以这个问题为问题来解决对iOS开发进行熟悉。

我喜欢边解决问题边学习的方式还学习新知识，这次iOS第一课，我准备解决项目中遇到的Pod仓库的问题，团队早就想建立一个Pod仓库，因为有些Pod开源项目并不维护了，所以使用`pod install`安装的依赖还需要手动修改一下才能使用，这个不是一个规范的操作。

我猜测是和Android/Java服务器中的maven仓库，可以自建，也可以采用第三方大厂的，比如阿里云的。估计也没有什么费用，因为目前阶段这样使用比较好。

我来画一个对比关系，更进步了解它们之间的不同之处。

| 语言 | Android | Java | iOS/Pod |
| ---- | ------ | ------ | ------ |
| 形式 | jar | jar | OC/Swift源码 |
| 主流 | bintray/maven | bintray/maven | CocoaPods |

对于Android或者Java服务器，需要自建私仓的情况是，需要对第三方库进行一些修改；需要将自己的代码做成库；iOS也类似。

Podfile例子
```podfile
platform :ios
 pod 'AFNetworking',    '~> 2.0.0'
 pod 'CocoaLumberjack', '< 1.7'

 target 'MyApp'
```

build.gradle子
```gradle
implementation 'org.greenrobot:eventbus:3.2.0'
```

由于Pod仓库管理的是C代码，应该会更加方便创建。

# Swift5.8版本报错
```Podfile
pod 'SwiftChart', '~> 1.0.1'
```

```
'kCALineJoinBevel' has been renamed to 'CAShapeLayerLineJoin.bevel'
```

| ![有帮助的截图](/assets/xcode_swift_chart.png) |
|:--:|
| *SwiftChart* |

查得仓库地址为：https://github.com/gpbl/SwiftChart

`2018.10.21`修改的此bug代码，最新tag1.0.1是`2018.1.10`号，依照我的性格，我尽可能先不搭建仓库的仓库，只是修改一下让pod工具能找到即可。

`fork`之后，在最后的commit上打上了`1.0.2`的tag，如下：
```
https://github.com/kangear/SwiftChart/releases/tag/1.0.2
```

又在网上查到如何指定仓库地址([CocoaPods中Podfile语法][1])，然后就指定了，最后的修改如下：
```Podfile
   pod 'SwiftChart', :git => 'https://github.com/kangear/SwiftChart.git', :tag => '1.0.2'
```

| ![有帮助的截图](/assets/swiftchart_kangear.png) |
|:--:|
| *SwiftChart指定仓库地址* |


经过测试OK。又突发奇想，只指定tag，那么能指定`commit`吗？如果可以的话，我还可以指定到原仓库地址，如下：
```Podfile
   pod 'SwiftChart', :git => 'https://github.com/gpbl/SwiftChart.git', :commit => '4949a94'
```

| ![有帮助的截图](/assets/1637311957845.jpg) |
|:--:|
| *SwiftChart指定仓库commit* |

那么答案就有了，也不需要创建私有仓库，只需要指定一下`commit`即可，如下：

| ![有帮助的截图](/assets/Podfile_swiftchart.png) |
|:--:|
| *SwiftChart完美配置* |


[1]: https://www.jianshu.com/p/900db3060f0f
