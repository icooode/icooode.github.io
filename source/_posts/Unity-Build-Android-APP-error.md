---
title: Unity Build Android APP
date: 2019-11-10 19:24:38
tags: [Unity, Sdk Manamager, Vuforia]
categories:
- Unity
- Android
---
## 前言
- 原先我愉快地使用着unity2017de的LTS（稳定版）
- 但不知道为什么vuforia无法显示识别图
- 于是我就把2017的Unity给卸载了
- 卸载了再打包随之问题也浮现出来了...

跟随我的文字去看看如何解决吧～

<!--more-->

## 遇到问题
升级到新版本后，第一件事情我做的是切换到安卓环境然后试试能否成功打包APK文件。报错了，提示我当前Sdk tools < 26.2.6。我懵逼了。
显然我并没有成功打包出APK文件，不然我为什么会在这写博客，你说是吧，哈哈哈。
而且我发现也有很多人没成功打包出来，百度，谷歌等搜索引擎也没搜索到相应的解决方案，也有可能是我搜索技术，英文表达方式有限，所以没搜索出来，那没办法只好自己找办法。

## 开干

### 发现

Sdk Manager是安卓的所以得去下载。
我直接百度的SDK Manager出现的页面就是[sdk manager](https://developer.android.google.cn/studio/command-line/sdkmanager)，点进去发现这个是命令行，第一次我在其他电脑上给配置成功了，但是到我自己电脑上却失败了。所以这个办法肯定是可行的。
<center>![下载](https://i.loli.net/2019/11/10/f6eJE89PYIcUvxH.png "下载")</center>

### 下载命令行版SDK Manager
[点击跳转下载链接](https://developer.android.google.cn/studio)，然后快速下拉到`Command line tools only`这个地方，下载命令行的[SDK Manager](https://dl.google.com/android/repository/sdk-tools-windows-4333796.zip)。
下载好后，在某个盘符下建立Sdk Manager文件夹，将下载过来的压缩包解压出来。此时你的路径结构应该是这样：
`Sdk Manager > tools`
我们需要快速通过在cmd中定位到当前路径，所以我们要进`/tools/bin`路径下，在当前地址栏输入`cmd`，这样我们就快速定位到当前路径。

### 下载所需的环境
[当前代码参考](https://developer.android.google.cn/studio/command-line/sdkmanager)

```bash
sdkmanager "platform-tools" "platforms;android-28" # 这一步会需要你输入y，确认是否进行下载
y # 所以输入y，并且回车

# 耐心等待下载完成

sdkmanager "build-tools;29.0.0"
# 大功告成
```

此时，我们已经完成本次文章想达到的目的了～恭喜你！

## 大功告成
大功告成！可以在Unity打包你的Android程序了。
