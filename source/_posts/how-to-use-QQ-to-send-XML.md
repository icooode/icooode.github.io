---
title: 如何发送XML到QQ上面
date: 2019-08-24 00:24:13
tags: [XML, QQ]
category: XML
---
> 阅读本文前提是你已经知道如何将发送XML到QQ上面

如果你不会的话，其实这个也很简单，就下载个机器人即可。是吧？很简单吧。
废话不多说，开始正文。
<!--more-->

# 1、寻XML、JSON代码
你得通过某种途径获取XML代码或者JSON格式的数据。
我是通过[侠客行](http://y-8.top/)这个网站寻找XML、JSON代码。

# 2、寻利器
下载机器人。
我用的是[cleverqq（原IRQQ）](https://www.cleverqq.cn/)。

# 3、寻插件
顾名思义，寻找能发送XML或者JSON的插件咯。
我使用的是菜单自定义_文本XMLjson [百度云地址](https://pan.baidu.com/s/1WgN0Wkk-ofWGQG1PijfMkw)

# 4、技术总结
**1、只能使用JSON格式。**
**2、内部的图片资源只能使用HTTP，不能使用HTTPS。**
**3、一般都是修改preview和icon里的值**

---
```json
# 仅做参考
{
"app":"com.tencent.structmsg",
"desc":"新闻",
"view":"news",
"ver":"0.0.0.1",
"prompt":"98k.org",
"meta":{"news":
	{"title":"98k.org",
	 "desc":"98k.org",
	 "preview":"https://98k.org/98k.png?ak=5cf900c4a2096",
	 "tag":"98k.org",
	 "jumpUrl":"98k.org",
	 "appid":100490701, 
	 "app_type":1,
	 "action":"",
	 "source_url":"",
	 "source_icon":"98k.org",
	 "android_pkg_name":"com.zhihu.android"
	 }
	},
"config":{"forward":true,"type":"normal","autosize":true}}

```

[更多示例下载地址](https://pan.baidu.com/s/13zc8Vbs1U_v4AOJv1Ga8vw)
