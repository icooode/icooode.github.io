---
title: 如何在life主题上启用Disqus评论
date: 2019-08-15 14:17:17
tags: [Disqus, Hexo]
category: 博客杂谈 
---
如何在life主题上启用Disqus评论
<!--more-->
## 如何正确的配置hexo->life主题Disqus评论
```bash
# Disqus配置，填是否开启和，你的Disqus站点名
disqus:
  enable: true
  name: your-nickname
```
我查了下，有人说这个是你的username，也就是在[Disqus常规](https://disqus.com/admin/settings/general/)下的Account。
我将主题内_config.yml修改成username，修改保存后，发现无法加载出Disqus评论。
于是我又查啊查，终于...我找到了（请看）：*请看参考文章第一篇。*
于是我修改了我的配置文件：
```bash
disqus:
  enable: true
  name: blog-your-nickname-com.disqus.com
```
修改之后发现是可以正常显示，但是问题它又来了，HTTPs协议报此网站不安全。
谷歌还能加载评论，但是显示不安全。
火狐直接就拦截了请求。
Hmm?我的心情就爆炸了。
我通过控制大法发现它的核心其实是请求一个JS文件，达到最后呈现评论的效果。但是我发现我的请求链接似乎有点怪怪的...我的心情：？？？，什么鬼（详情吐槽请看B站张全蛋，恩，跟那个差不多）
` https://blog-you-nickname-com.disqus.com.disqus.com/embed.js `
虽然心情很爆炸。但是我觉得我整个网站只有配置文件有影响这个，所以我把配置文件里的disqus.com干掉了。
```bash
disqus:
  enable: true
  name: blog-your-nickname-com
```
再刷新，正常显示以及HTTPs都显示正常。

## 总结

**1、配置文件内name是你的Shortname，而不是你的username。**
**2、Disqus需要科学上网，并且登录某一方平台才能参与评论（例如，谷歌，脸书）**
**3、Disqus挺好用的**


---
参考文章：
[1、正确的设置了disqus_shortname，界面却无法加载disqus](https://github.com/iissnan/theme-next-docs/issues/86)
