---
title: electron 发起系统信息通知提示
date:  2020-05-30 13:29
tags: [electron, Javacsript]
category: 前端
---
> 本着想做点啥，开始想electon既然是桌面级别程序，是不是可以发起系统信息通知呢...
<!--more-->

## 效果展示
![弹窗效果展示](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/electron/200530051807.png)

我在百度搜索到，electon如果需要用到这个`Notification`功能，那么需要注册个AppID，看到这里我是一脸懵逼(找不到那个问题贴了)。
又百度发现，害，原来这么简单啊。
1、 先在你的`package.json`里添加：
```json
"build": {
    "appId": "com.example.app"
}
```
经我后面测试，发现这段其实有没有都是不影响最后弹窗效果的。

2、然后在你的入口`main.js`里，添加`app.setUserModelId("com.electron.这里改成你package.json里name");`这串代码。

3、最后，在你需要弹窗的地方，添加以下代码（我是绑定给按钮，所以我在按钮点击事件里添加的）：
```js
$testBtn.on('click', () => {
  let option = {
    title: "你订阅冰黎的博客更新了",                          // 通知标题
    body: "更新内容blablala的",                              // 内容
    icon: "../favicon.ico",                                 // 图标
    href: 'https://www.cnblogs.com/binglicheng/'            // 地址
  };

  // 创建通知并保存
  let hhwNotication = new window.Notification(option.title, option);

  // 当通知被点击时
  hhwNotication.onclick= function(){
      // TODO something...
  }
})
```
## 至此，本章完。
这是个我集合两个人的代码的文章。也是做个`demo`笔记。

## 参考网站
[electron win 10添加AppID](https://malagege.github.io/blog/2018/10/01/electron-win-10%E8%A8%AD%E5%AE%9A%E9%80%9A%E7%9F%A5-AppUserMOdelId-electron-builder%E7%9B%B8%E9%97%9C%E8%A8%AD%E5%AE%9A/)
[electron 消息弹窗代码](https://www.jianshu.com/p/32ccce158401)
