---
title: js读取usb扫码枪数据
date: 2020-05-20 13:45
tags: Javascript
category: Javascript
---
js读取usb扫码枪数据。
<!--more-->
条码扫描器其实就是一种输入设备，跟键盘一样。在控制台打印扫描过程，可以看出，扫描过程就像是在键盘上敲击相应的键，keycode和键盘是一一对应的，只是输入速度(间隔时间)比物理键盘输入要快得多。我们可以通过监听输入间隔时间，来判断到底是键盘输入还是扫描输入。

扫码枪输入的时间间隔一般在10毫秒以内，物理键盘输入要远大于这个数值，通常为80毫秒以上。因此，当输入间隔时间小于30毫秒时，判断为扫码枪输入，其余情况判断为键盘输入。
```
window.onload = function () {// 获取扫描的二维码
  var code = "";
  var lastTime, nextTime;
  var lastCode, nextCode;
  document.onkeypress = function (e) {
      nextCode = e.which;
      nextTime = new Date().getTime();

      if (lastCode != null && lastTime != null && nextTime - lastTime <= 30) {// 扫码枪
          code += String.fromCharCode(lastCode);
      } else if (lastCode != null && lastTime != null && nextTime - lastTime > 100) { // 键盘
          code = "";
      }

      lastCode = nextCode;
      lastTime = nextTime;
  }
  this.Template_rendering = function () {
      this.onkeypress = function (e) {
          if (e.which == 13) {
              console.log(code);
              // $('#code').text(code)
              readcode({code: code}); // 调用readcode方法
              code = "";
          }
      }
  }
  this.Template_rendering();
};
```
