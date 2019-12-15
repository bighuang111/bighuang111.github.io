---
layout:     post
title:      "root 三星S10"
subtitle:   "每天都要变博学的小黄"
date:       2019-12-15 15:04:00
author:     "LittleHuang"
header-img: "img/in-post/post-eleme-pwa/eleme-at-io.jpg"
header-mask: 0.3
catalog:    true
tags:
    - 工具
    - Android
typora-root-url: ..\img\root-samsung
---

# 如何root三星S10

root已经成功，参考链接如下：

http://bbs.gfan.com/android-9558898-1-1.html 这个似乎是一个靠谱的文档

##### 解锁三星s10 系列Bootloader

1.进入设置->关于手机->软件信息->编译编号(点击7次)

2.设置->开发者选项，打开“OME解锁”以及"USB调试"

3.先关机，然后同时按住 音量down + Bixby，接着连接USB到电脑，手机启动下载模式。

4.注意是长按 音量up(点击是rom里的步骤)，将解锁引导加载程序，会擦除所有的数据和重新启动设备进入系统。

5.查看"OME解锁"选项，如果变成灰灰色状态，这一步成功了。

##### 安装Magisk并且root

1.下载手机官方固件，我的是在[迷你手机网](https://www.netded.com/)下载的，这里注意要选择新的版本的固件，如果低于当前手机版本，将会报错(我在rom手机的时候出现了版本过低的错误，不清楚这里会不会，反正新版本肯定没问题)。

2.下载[Magsik](https://github.com/topjohnwu/Magisk/releases),使用在common文件夹下的.apk

3.在手机中安装Magsik.apk

4.将系统固件包中的AP文件放到手机的download文件夹下，打卡Magsik，选择主页面上面的安装->安装->选择并修补一个文件，打开手机的文件夹，进入download目录，找到AP文件

5.将/Download/magisk_patched.tar复制到电脑上。

6.下载最新的[Odin](https://odindownload.com/),我使用的是从[迷你手机网](https://www.netded.com/)下载的版本。

7.重启手机进入下载模式（音量down + Bixby，USB链接电脑），

![root-samsung-s10-1](/root-samsung-s10-1.jpg)





线刷rom成功，安装教程如下

https://www.netded.com/guide/201907/3143740.html



安装的资源在黄小宇/rom-G9700文件夹下

