---
title: HbuilderX连接夜神模拟器
date: 2019-09-06 10:19:06
tags: [模拟器, Ide]
category: Ide
---
> HbuilderX连接夜神模拟器
<!--more-->
# 一、下载夜神模拟器
[下载地址](https://www.yeshen.com/cn/download/fullPackage "点击下载")

# 二、下载Hbuilder
[下载地址](https://www.dcloud.io/hbuilderx.html "点击下载")
点击DOWNLOAD然后选择***APP开发版***，耐心等待下载即可。

# 三、启动HbuilderX、夜神模拟器
在这一步，我将默认你已经打开了HbuilderX和夜神模拟器，否则将无法进行下一步操作。

# 四、配置HbuilderX
在这一步，你将配置好启动的浏览器项。
点击任务栏工具->设置->运行配置->浏览器运行配置。
![浏览器运行配置](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/hbuilder/2019090601.png)
一般来说谷歌浏览器是在图中那个路径下。

# 五、配置模拟器
到了最令人紧张刺激兴奋的环节，这一步后你将可以用HbuilderX连接上夜神模拟器啦。

1.首先你先进入夜神模拟器bin模拟器下
&emsp;a. 右键你桌面上夜神模拟器快捷方式->选择属性（R）->打开文件所在位置（推荐）。
&emsp;b. 或者直接通过打开我的电脑->寻找夜神模拟器安装路径。

2.打开cmd窗口
&emsp;a. 在当前资源管理器地址输入cmd（推荐）
![cmd](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/hbuilder/2019090602.png)
&emsp;b. win+r->cmd->通过cd定位到夜神模拟器bin文件夹目录下（略微麻烦且复杂）

3.连接
```bash
# 在cmd中运行下面代码 
nox_adb connect 127.0.0.1:62001
```
如果没报错，跳到第五步。
如果报错了，说明夜神模拟器端口不对。

4.获取端口
```bash
# 打下面代码查看当前夜神模拟器端口（请确保到这一步时，你的夜神模拟器现在还是开着的）。
nox_adb devices
```

5.修改HbuilderX内端口
点击任务栏工具->设置->运行配置->Android模拟器端口。
![devices](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/hbuilder/2019090603.png)
![Android模拟器端口](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/hbuilder/2019090604.png)

6.再次连接
```
# 这里端口号取决于第4步获取到的端口
nox_adb connect 127.0.0.1:52001
```

7.到HbuilderX目录
找到在HbuilderX在桌面上的快捷方式，进入到它的根目录，进入到下面这个路径。然后在地址栏输入cmd。
***\HBuilderX\plugins\launcher\tools\adbs***
```bash
# 跟夜神模拟器相连。
# 注意：这里端口号参考第四步。
adb connect 127.0.0.1:62001
```

# 六、使用模拟器
到这一步，你已将大功告成了，就差应用啦。
点击工具栏->运行->运行到手机或模拟器->运行。
![运行](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/hbuilder/2019090605.png)

# 七、大功告成
大功告成，耐心等待即可。

---
参考文章：
[HBuilder使用夜神模拟器调试Android应用](https://www.yeshen.com/faqs/HJwD1yQe- "点击浏览")
[HBuilder使用夜神模拟器调试Android应用](https://www.cnblogs.com/stulzq/p/5123875.html "点击浏览")
