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

7.重启手机进入下载模式（音量down + Bixby，USB链接电脑），点击AP选择magsik_patched.tar文件，进入选项options 取消“Auto Reboot”,点击start。

![](https://github.com/bighuang111/bighuang111.github.io/blob/master/img/root-samsung/root-samsung-s10-1.jpg)

![](https://github.com/bighuang111/bighuang111.github.io/blob/master/img/root-samsung/root-samsung-s10-2.jpg)

8.完成后，按住电源 + 音量down 退出下载模式，当屏幕黑掉后立即按下 音量up + 电源 + Bixby，当屏幕出现警告时，释放电源和Bixby,但继续按住音量up，直到进入恢复模式。（这里的几步都是按循序执行的，失败后没关系，把握住警告页面后进入黑屏的时机，重来就好了）

9.使用"音量上"和"音量下"按钮在选项之间移动。 找到“Wipe data/factory reset” （必须是这个，而且这个恢复模式里面至少10条可选，如果你进入了只有3条可选的模式，那么就是错误的，得重复8步骤，或者回到5步骤开始，我开始就这里弄错了），按下电源按钮执行擦除。

10.完成擦除后，选择"重新启动系统"（第一个），并立即按下音量上 + Bixby + 电源按钮一起，当警告屏幕出现时，释放按钮（失败了就重试）。手机可能会自动重启一次，不用管它，是正常的。

11.进入系统，完成初始设置，这时候应该能找到Magisk Manager，找不到的话重新安装一次，连上网，进入Magisk Manager等待最后的自动设置。

12.长按Magisk Manager桌面图标就可以添加超级权限了！搞定！













线刷rom成功，安装教程如下

https://www.netded.com/guide/201907/3143740.html



安装的资源在黄小宇/rom-G9700文件夹下

