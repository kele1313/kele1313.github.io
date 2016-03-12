---
layout:     post
title:      "首先记录一下博客环境的搭建"
subtitle:   "第一次使用jekyll和markdown写博客"
date:       2016-03-11 15:00:00
author:     "rage"
header-img: "img/kahra2.jpg"
tags:
    - 生活
---

> 首先请叫我博主。。。

## 为什么要用这么麻烦的方式写博客

* 厌倦了大众博客，内容杂乱，还老有小广告
* 作为非程序员体验一下程序员的工作方式
* blogging like a hacker
* 服务是免费的，而且可以高度自制


## 开始搭建环境

为了能在各种机器上发布博客，本博主下决心从windows平台搭起，（这些开源项目很少照顾windows平台，难免会遇到不少坑）然后Linux下就不说了，基本没坑:D

嗯，[win7上部署jekyll](http://jekyll-windows.juthilo.com/)
这个网站介绍如何在windows环境下安装jekyll，非常详细。然而网页上说虽然官方网站上给出了在windows下安装的方法，但这个方法仍然是非官方的。。。程序员的逻辑果然严谨，但是然并卵吧

### 首先安装ruby和devkit

[下载ruby](http://rubyinstaller.org/downloads/)，注意版本号分32位64位，用2.0.0的稳定些，新的也有，想尝试的也可以试试

[下载devkit](http://rubyinstaller.org/downloads/)，同样要区分处理器位数

**ruby安装时注意勾选**  

- [x] *add ruby executables to your path*

 - [x] this is a complete item

假设路径全都默认到c盘根目录
命令行下敲：

```cmd
cd c:\rubydevkit                      //devkit解压后的位置
ruby dk.rb init                       //ruby装好后就可以在命令行下执行了
ruby dk.rb install                    
```

### 安装jekyll

```cmd
gem install jekyll
```
安装gem时由于要连接Rubygems官方源，所以墙内的朋友会在这里第一次碰壁。。。。呵呵，没错后面还会碰

删除官方源，增加淘宝源，放心使用，属于阿里云旗下的

```cmd
gem sources --remove https://rubygems.org/
gem sources -a https://ruby.taobao.org/
gem install jekyll
```
如果gem install jekyll还是报错，可能是ssl证书认证问题，这里就是第二个坑
可以把刚才的淘宝源删掉，再增加http://ruby.taobao.org/，或者http://mirror.bit.edu.cn/rubygems/（华东科技大学的rubygem 镜像源），或者http://ruby.sdutlinux.org/（山东理工rubygem 镜像源）注意保证sources 里只有一个源，用gem sources -l 可以查看源列表

然后cd到网站目录，输入 jekyll build会生成静态页面

```cmd
jekyll build                         //生成静态页面
jekyll serve                         //开启http服务，访问127.0.0.1:4000可以预览你的页面
```
推荐两个不错的页面，都是开源的，可以拿来自己修改
[hux](https://github.com/Huxpro/huxpro.github.io) | [davidtmiller](https://github.com/davidtmiller/davidtmiller-website)

## 更新博客

```bash
$ git clone https://github.com/username/username.github.io.git //首先取得代码
$ cd ~/username.github.com //定位到你blog的目录下
$ git pull origin master //以后用来同步远程文件，刚执行完第一条命令可以略过
$ git status //查看本地自己修改了多少文件
$ git add . //添加远程不存在的git文件
$ git commit * -m "what I want told to someone"//添加到工作区并且做说明
$ git reset --hard 哈希值//如果不小心commit了一个不需要commit的文件，可以对其进行撤销。哈希值通过git log 命令获取
$ git log //上条命令中的哈希值通过此命令获取
$ git push origin master //一切就绪后更新到远程服务器上
```
深入了解可以参考https://jekyllrb.com/docs/home/

