---
title: Ubuntu 12.04 安装搜狗拼音输入法
date: 2014-05-19 15:53:41
tags:
    - 输入法
categories:
    - Ubuntu
---

新出的linux下的搜狗输入法，颇感兴趣，这里作为记录。 

### 安装fcitx
ubuntu12.04默认源中的fcitx版本较旧，安装新版本的fcitx。 

    sudo add-apt-repository ppa:fcitx-team/nightly
    sudo apt-get update 

如果已经安装了旧版本的fctix，更新: 

    sudo apt-get upgrade 

<!--more-->

更新后，需重启或注销重新登陆。 

未安装，直接安装： 

    sudo apt-get install fcitx

安装googlepinyin和sunpinyin（个人习惯，作为备用）： 

    sudo apt-get install fcitx-googlepinyin
    sudo apt-get install fcitx-sunpinyin

切换输入法框架为fcitx： 

    im-switch -s fcitx 

### 卸载ibus
ibus和fcitx共存时老有一些莫名其妙的bug，所以卸载ibus。 

    killall ibus-daemon
    sudo apt-get autoremove ibus ibus-sunpinyin

如果你使用的桌面是gnome，请暂时先不要卸载ibus-gtk3，据说会导致进步了系统。 

如果上一步没有重启过，重启或者注销重新登陆。

### 安装搜狗拼音
* [下载安装](http://pinyin.sogou.com/linux/?r=pinyin) 

### 遇到的问题

小企鹅右键设置启用搜狗pinyin，输入的时候提示： 

> 請啓用fcitx-qimpanel面板程序，以便更好的享受搜狗輸入法！

解决办法：
重启 fcitx 切换到 qimpanel，同时开启 qimpanel

    fcitx -r --enable fcitx-qimpanel
    fcitx-qimpanel 

有时重启系统后，输入法没有输入框的现象，只能盲打，我的解决办法是kill掉fcitx-qimpanel，然后重新启动，不可以的话就多kill掉几次`ps -ef | grep qim`。
