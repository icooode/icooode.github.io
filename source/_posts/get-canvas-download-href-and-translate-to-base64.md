---
title: 前端实现获取canvas下载地址以及下载base64图片格式到本地功能
date: 2020-05-24 20:33
tags: [canvas, base64]
category: 前端
---
前端实现获取canvas下载地址以及下载basse64图片格式到本地功能。
<!--more-->
## 全部代码
```js
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>html2canvas，实现下载</title>
</head>

<body>

    <ol class="ol">
        <li>test</li>
        <li>test</li>
        <li>test</li>
        <li>test</li>
        <li>test</li>
        <li>test</li>
        <li>test</li>
        <li>test</li>
        asdasdasdasdas
    </ol>

    <a href="javascript:;" class="btn">点我哦</a>
    <a href="javascript:;" class="btn2" download="ddd.png">下载</a>

    <!-- 引入Jquery -->
    <script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
    <!-- 引入html2canvas -->
    <script src="https://cdn.bootcss.com/html2canvas/0.5.0-beta4/html2canvas.js"></script>
    <script>

        $(function () {
            html2canvas(document.querySelector('.ol')).then(function (canvas) {
                $('.ol').remove()    //移除页面上的该元素
                canvas.id = "canvas";
                var dataURL = canvas.toDataURL("image/png");
                $(document.body).data('url', dataURL);
                document.body.appendChild(canvas);    //像页面中添加转为canvas之后的元素
            })

            $('.btn').on('click', function () {
                var dataURL = $(document.body).data('url');
                var tmpUrl = "data:application/octet-stream;base64" + dataURL;
                $('.btn2').attr('href', tmpUrl);
                // window.open(tmpUrl);
            })
        });
    </script>
</body>

</html>
```
### 核心代码解析：
1. `download="ddd.png"`，***ddd就是文件名，.png则是文件后缀名***。
2. 这样就是在数据前面加了`"data:application/octet-stream;base64" + dataURL`，就可以直接下载了。
3. PC上测试可以下载，手机上也测试可以下载。


---
参考文章：
一：https://zhuanlan.zhihu.com/p/28176700
