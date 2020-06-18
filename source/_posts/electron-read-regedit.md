---
title: electron-read-regedit
date: 2019-10-15 13:26:26
tags: [Electron, Regedit]
categories:
- 前端
- Electron
---
## 前言
就是分享一下获取注册表的代码。
<!--more-->
## 代码
```js
const regedit = require('regedit')
const regeditPath = 'HKLM\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\'

// 开始获取注册表
regedit.list([regeditPath], function (err, data) {
  if (err) {
    console.log('err' + err)
  }
  // 遍历目录
  for (let item in data) {
    // data[item].keys.length 长度
    let keys = data[item].keys
      // 获取相对应的项目名字
      // keys.length
    for (let i = 0; i <= keys.length; i++) {
      let keyName = keys[i]
      // console.log(keys[i])

      // 防止空项目报错
      if (keyName === undefined) {
        break
      }

      regedit.list([regeditPath + keyName], function (err, data) {
        if (err) {
          console.log('err' + err)
        }
        // 将当前数据存放到数组
        let tmpArr = []
        for (let i in data) {
          tmpArr.push(data[i])
        }

        let tmpValues = tmpArr[0].values
        if (tmpValues !== undefined) {
          // 首先，数据数量必须大于5，过滤无效注册表
          // 其次，我们要取的程序名字不能为空，也是防止报错
          if (Object.keys(tmpValues).length >= 5 && tmpValues['DisplayName'] !== undefined) {
            // console.log('长度 ============= ' + Object.keys(tmpValues).length)
            // console.log('详细数据 =========== ' + tmpValues['DisplayName']['value'])
            // console.log('总数据 ============ ' + tmpValues)
          }
        }
      })
    }
  }
})
```
