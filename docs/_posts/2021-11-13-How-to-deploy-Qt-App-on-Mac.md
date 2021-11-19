---
layout: post
title:  "Mac上打包Qt程序"
date:   2021-11-13 09:55:05 +0800
categories: mac
typora-copy-images-to: ../asserts
typora-root-url: ../
---

以前写的一个Qt程序，移植Windows下的一个名字叫sscom的串口助手到Linux下了。试了一下在Mac上也可以编译发布。这里记录打包过程。

| ![有帮助的截图](/assets/Selection_441.png) | 
|:--:| 
| *sscom* |


# 安装Qt环境
```shell
% brew install qt5
```

# 添加环境变量
```shell
% export PATH=$PATH:/usr/local/Cellar/qt@5/5.15.2_1/bin
```

# 下载源码和编译
```shell
% git clone https://github.com/kangear/sscom.git && cd sscom
% qmake
% make
```
这时会生成`sscom.app`可以在本mac上运行。如果像要在其它mac上也运行，需要把必要的库文件也打进来。

# 打包依赖
`macdeployqt`环境中已有的小工具，不需要从第三方下载。
```shell
% macdeployqt sscom.app
```

| ![有帮助的截图](/assets/a9c38205fd26bab635168782ec52443.jpg) | 
|:--:| 
| *sscom.app* |

如果出现如下，说明`当前用户`没有`管理`权限，切换为有`管理`权限的用户就可以了
```
% macdeployqt sscom.app
ERROR: Could not find bundle binary for "sscom.app"
ERROR: "error: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/otool-classic: can't open file:  (No such file or directory)\n"
ERROR: "error: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/otool-classic: can't open file:  (No such file or directory)\n"
ERROR: "error: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/otool-classic: can't open file:  (No such file or directory)\n"
WARNING:
WARNING: Could not find any external Qt frameworks to deploy in "sscom.app"
WARNING: Perhaps macdeployqt was already used on "sscom.app" ?
WARNING: If so, you will need to rebuild "sscom.app" before trying again.
ERROR: Could not find bundle binary for "sscom.app"
ERROR: "error: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/strip: can't open file:  (No such file or directory)\n"
ERROR: ""
% 
```

这时`sscom.app`中就带有了库依赖，拷贝到其他mac上也能运行了。如果需要正规发布，还需要打成`dmg`包。

# 制作dmg镜像
```
打开Disk Utility，选择File->New Image->Blank Image 来创建对应的dmg镜像
创建出来的.dmg文件可以双击打开
在空白处点击右键选择 Show View Options 可以打开图中左侧弹窗，对dmg信息进行编辑
按照步骤1将需要在dmg中展示的背景图拖入到指定位置
然后将.app文件拖到当前dmg中
创建Applications的替身并拖到当前dmg中
接下来就是要让app显示咱们希望展现的icon
可以上 https://cloudconvert.com/png-to-icns 将1024x1024的png图片转换成Mac OSX的图标格式 .icns
将生成icns拷贝到.app的Resource目录，并修改Info.plist文件中的CFBundleIconFile对应的值为icon文件的名字
在.app上右键显示详情，并将icns文件拖到图标位置，即可让app显示出其图标
```
来自：https://zhuanlan.zhihu.com/p/38620218

[1]: https://docs.appimage.org/packaging-guide/converting-binary-packages/index.html#ref-convert-existing-binary-packages
[2]: https://appimage-builder.readthedocs.io/en/latest/intro/tutorial.html