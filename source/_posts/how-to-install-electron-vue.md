---
title: 安装electron-vue之踩坑
date: 2019-10-13 18:01:08
tags: [Windows, ELectron, Vue]
categories:
- 前端
- Electron
---
## 前言
我想搞一个Windows桌面软件，但是E语言无法读取到注册表，就只能选择用这个。
- 什么？你问我学我unity的为什么不用C#写。
- 答：我不会啊。
- 为什么用electron
- 答：因为我除了unity好好学之外，还有就是JS好好学了。
<!--more-->

## 环境
不知道你们会选择什么环境，我选择的是linux(ubuntu)作为我的开发环境。
Electron由Node.js+Chromium+Native APIs构成。
### Node.js
因此你需要Node.js。详细的安装请自行百度。
By the way, 你的安装路径中最好别带有中文字符，如果不会的话，傻瓜式安装即可。

## 安装Electron
### npm
我尝试过用npm下载Electron，不过那速度很美丽。所以我选择了淘宝国内镜像。
### cnpm
通过npm安装cnpm...这速度当然非常美丽。
建议边吃饭边看电视边看小说，然后等待。
```bash
 $ npm install -g cnpm --registry=https://registry.npm.taobao.org 
```
### 通过cnpm安装Electron
全局安装electron，可能会有权限问题所以使用sudo来进行安装。
```bash
$ sudo cnpm install -g electron
```

## 启动Electron
### 通过Electron提供的快速工程打开一个简单的electron项目
[教程地址](https://electronjs.org/docs/tutorial/first-app#%E5%B0%9D%E8%AF%95%E6%AD%A4%E4%BE%8B "打开教程")
当然你这一步骤需要git，所以你还额外需要安装git。百度一下，自己动一下手。
```bash
# 克隆这仓库
git clone https://github.com/electron/electron-quick-start
# 进入仓库
cd electron-quick-start
# 安装依赖库
npm install
# 运行应用
npm start
```
如果程序正常运行的话，你会看见弹出一个electron工程窗口！
### 大功告成
完结！~开玩笑的~
当然，你已经成功创建了一个electron项目，即使他还是那么简陋。所以它还仅仅不够。
以下[代码出处](https://molunerfinn.com/electron-vue-1/#electron-vue%E5%AE%89%E8%A3%85 "访问代码出处")
## 安装Electron-vue
```bash
# 如果你没有vue-cli的话需要全局安装
npm install -g vue-cli
# 然后使用vue-cli来安装electron-vue的模板
vue init simulatedgreg/electron-vue my-project

# 安装依赖
cd my-project
yarn # or npm install
# 进入开发模式
yarn run dev # or npm run dev
```
### npm install~(正文开始)~
安装依赖，实际上我是在这步才安装cnpm，因为npm的下载速度实在太美丽。
### cnpm install
安装所需的依赖。然而，我使用这步安装完所有的依赖，但我执行cnpm run dev又出问题了。所以我不得不安装yarn。
### yarn
#### 安装yarn
```bash
# 我是使用aptitude来安装，win/mac请忽视这一步
$ sudo aptitude update && sudo aptitude install yarn
# or sudo apt-get update && sudo apt-get install yarn
```
#### 踩坑yarn
```bash
# 当我cd到my-project文件
$ yarn
00h00m00s 0/0: : ERROR: There are no scenarios; must have at least one.
# 却收获一个错误
# 经过搜索可能是yarn版本低的问题
```
```bash
# 当然，如果你没报错的话，请忽视这一步骤
$ sudo apt remove yarn

$ curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -

$ echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

$ sudo apt update && sudo apt install yarn
```

``` bash
# 最后在执行下yarn
$ yarn
# 但是我yarn在下载依赖的时候，报错了
libgconf-2.so.4: cannot open shared object file: No such file or directory
# 提示缺少libgconf-2.so.4
# 此时只需要下载libgconf2-4即可
$ sudo apt-get install libgconf2-4
# 进入开发模式
$ yarn run dev
```
## 大功告成
大功告成！





---
参考文章：
一、[官方环境配置教程](https://electronjs.org/docs/tutorial/development-environment "官方教程")
二、[Electron-vue入门](https://molunerfinn.com/electron-vue-1/#%E5%89%8D%E8%A8%80 "点击打开")
三、[cnpm淘宝镜像](https://npm.taobao.org/ "访问cnpm淘宝镜像")
四、[StackoverFLow](https://stackoverflow.com/questions/53471063/yarn-error-there-are-no-scenarios-must-have-at-least-one "访问stackoverflow")
五、[libgconf-2.so.4](https://blog.csdn.net/eCaiFu800/article/details/79313058?utm_source=blogxgwz6 "访问csdn")
六、[Electron构建桌面应用](https://blog.csdn.net/qq_35559756/article/details/84058508 "访问csdn")
