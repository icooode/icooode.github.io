---
title: linux下设置mysql密码之密码正确也无法进入
date: 2020-05-08 12:10
tags: [mysql, linux]
category: [linux]
---
当你尝试了所有一切，其实都生效了，但你还是不能登进mysql里了，是不是感觉很气。
<!--more-->
我本打算用python里的pymysql然后在使用lpthw.web撸个普通的由python写的博客，然后我就开始了我这两天掉坑之旅。
只是因为pymysql连接mysql数据库被 `Access denied for user 'root'@'localhost'。`呵，无情的拦截。
其实是因为mysql没有设置密码。其实你是设置了只是还有地方没配置好。
我用了两种方式：
一是（这个是不需要进mysql）：
`mysql_secure_installation`
二是（这个需要进mysql里操作）：
`GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY '123456' WITH GRANT OPTION;`
`flush privileges;`
这两者其实都生效了，但你还是不用密码就登进mysql里了，是不是感觉很气。
`$ sudo mysql -u root # 进入你的mysql`
```
mysql> USE mysql;
mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root'; # 只要把plugin修改成mysql_native_password就好了
mysql> FLUSH PRIVILEGES;
mysql> exit;

$ service mysql restart # 重启mysql(windows则使用net stop mysql)
```

---
参考网站：
一：http://stackmirror.caup.cn/page/s1jf9ragkt9w
二：https://www.server-world.info/en/note?os=Ubuntu_18.04&amp;p=mariadb&amp;f=1
