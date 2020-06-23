---
title: badusb-digispark-ATTINY85
date: 2019-09-28 11:45:35
tags: [BadUSB, Digispark]
category: [博客杂谈]
---
BadUSB最早是在2014年的黑帽大会上研究人员JakobLell和Karsten Nohl提出并展示的。不同于老式的U盘病毒，它利用了USB协议中的一个漏洞，通过模拟键盘、鼠标、网卡等从而让目标电脑执行恶意代码，达到控住主机或者窃取敏感信息等目的。
<!--more-->

# 前言

知道badusb已经好久了，但是迟迟没有购买，原因嘛。。很简单：我菜嘛，怕买来了用不起来，怕需要驱动。。（但我还是在几个月后买了..）

# 购买

我用的是Digispark一个基于ATTINY85微控制器的USB开发板，体积小且价钱便宜。
淘宝一个差不多10块5吧。[淘宝地址](https://item.taobao.com/item.htm?spm=a1z09.2.0.0.bd8e2e8dWUGoEB&id=573691183135&_u=s2q1ujspea55 "点击打开淘宝")

# 开搞*~(踩坑)~*

## a.踩坑准备所需
- arduino(IDE) [下载地址](https://www.arduino.cc/en/Main/Software "点击下载IDE")
- digispark drive(驱动) [下载地址](https://github.com/digistump/DigistumpArduino/releases/download/1.6.7/Digistump.Drivers.zip "点击下载驱动")

## b.具体配置教程
- 请参考第一篇参考文章。
- 需要注意的就是在首选项内添加JSON。
- 下载好后选择Tools(工具) -> Borad(开发板) - > Digispark (Default - 16.5mhz) 
- 再选择Tools(工具) -> Programmer(编辑器) -> USBtinyISP

# 踩坑

## a.开始烧录
- 具体代码请参考第二篇参考文章。
- 拷贝好代码后，点击upload（注意这一步骤是不需要插着Digispark）。
- 等待arduion出现下面代码提示，具体意思：请插入你的硬件。
```bash
Running Digispark Uploader...
Plug in device now... (will timeout in 60 seconds)
```
- 耐心等待即可。

## b.开始踩坑
- 你会发现烧录成功后，烧录的代码只会执行一次,并且其他电脑不会自动安装驱动。(~抓狂~)
- 我加了相关的Q群，查了百度大量信息，最后发现可能是我的Digispark内置的Bootloader版本太低了。
- 具体升级Bootloader方法，请参考第三篇参考文章。
- 如果嫌弃下载慢的话，[蓝奏云](https://www.lanzous.com/b00n4a0ib "点击打开蓝奏云")密码:3k0e，我本来还想把IDE分享，结果大于180M无法上传，所以就只能自己慢慢下载～

## c.刷完固件
- 升级好Bootloader。
- 再烧录一次。
- 再用其他没有digispark驱动电脑试试

# 大功告成
大功告成！

***最后的声明：本人仅做研究，兴趣爱好。并分享我的踩坑经验。
未经允许不得传播。
本文仅供学习之用，不负任何法律责任。***

---
# 参考文章
一、 [7块钱的BadUSB](https://cloud.tencent.com/developer/article/1088490 "点击打开")
二、 [badusb的学习记录&入侵windows主机](https://lzy-wi.github.io/2018/06/12/badusb/ "点击打开")
三、 [DigiSpark更新Bootloader](https://blog.csdn.net/sxhexin/article/details/87914649 "点击打开")
