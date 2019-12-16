---
layout:     post
title:      "Android MediaCodec"
subtitle:   "每天都要变博学的小黄"
date:       2019-12-16 18:54:00
author:     "LittleHuang"
header-img: "img/in-post/post-eleme-pwa/eleme-at-io.jpg"
header-mask: 0.3
catalog:    true
tags:
    - 工具
typora-root-url: ..\img\root-samsung
---

# 搭建shadowsocks服务器

1.在vutrl官网上新建一个服务器，选择centos7，5$的就可以。

2.用putty连上服务器，执行以下三条命令

wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh

chmod +x shadowsocks.sh

./shadowsocks.sh 2>&1 | tee shadowsocks.log

加密模式 选择aes-256-cfb

3.去[shadowsocks](https://github.com/shadowsocks/shadowsocks/releases)下载最新的版本，填好在步骤二中输入的信息即可。

4.用完了记得destory掉服务器！！！你还是一个贫穷的小黄！！！





