---
title: 康虎云报表设计器设计出能读取多条数据的报表模板
date: 2020-05-25 15:37
tags: [康虎云, Javascript, 打印机]
category: [前端]
---
康虎云报表设计器设计出能读取多条数据的报表模板。
> 前言 康虎云是真的毒，全网几乎搜不到关于他的问题解决方案。
<!--more-->
## 设计器
![设计器](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/kanghuyun/200525072554.png)
以上是我的康虎云内所有字段。
1. `userInfo`
2. `feedback`
## 我的JSON数据格式：
```
{
  "template": "123.fr3",
  "ver": 4,
  "Preview": 0,
  "Duplex": 0,
  "Tables": [
    {
      "Name": "feedback",
      "Cols": [
        {
          "type": "int",
          "size": 0,
          "name": "id",
          "required": false
        },
        {
          "type": "str",
          "size": 255,
          "name": "question",
          "required": false
        },

      ],
      "Data": [
        {
          "id": 0,
          "question": "这是西服上装正面领子返修问题。05"
        },
        {
          "id": 1,
          "question": "这是西服上装背面袖子返修问题。08"
        },
        {
          "id": 2,
          "question": "这是西服上装其他返修问题。19"
        },
        {
          "id": 3,
          "question": "这是西服上装其他返修问题。20"
        },
        {
          "id": 4,
          "question": "这是西服上装其他返修问题。21"
        },
        {
          "id": 5,
          "question": "这是西服上装其他返修问题。22"
        }
      ]
    },
    {
      "Name": "userInfo",
      "Cols": [
        {
          "type": "str",
          "size": 255,
          "name": "userName"
        },
        {
          "type": "str",
          "size": 255,
          "name": "liushui"
        },
        {
          "type": "str",
          "size": 255,
          "name": "createTime"
        },

      ],
      "Data": [
        {
          "userName": "测试数据",
          "liushui": "1",
          "createTime": "2020/5/25 上午10:05:57",
        }
      ]
    }
  ]
}
```
## 效果图
### 这是我拉长明细数据 DetailData的效果
![效果图1](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/kanghuyun/200525073306.png)
### 这是我拉短明细数据 DetailData的效果
![效果图2](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/kanghuyun/200525073319.png)

## 顺带一嘴哈
如果右边没有显示数据和字段。也就是这个。
![数组字段](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/kanghuyun/200525074313.png)
那么我推荐你最好先把json数据模拟好。
1. 打开`康虎云路径/cfprint/cfprint.exe`文件。这一步是启动康虎云，如果你已经启动了则无视这步骤。
2. 双击***设计***，把你刚刚模拟好的JSON数据放进去，点击设计按钮，你就会发现右侧出现这些字段了。
![点击设计按钮](https://raw.githubusercontent.com/icooode/images-of-website/master/blog/kanghuyun/200525074713.png)

## 大功告成
这也算是大功告成了吧！

## 参考网站
http://www.khcloud.net/manaual/cfprint/index.html
