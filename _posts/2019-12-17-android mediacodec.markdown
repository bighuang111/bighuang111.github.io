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
    - mediacodec
    - Android
typora-root-url: ..\img\root-samsung
---

# android下硬解码h265视频（非.mp4）

android下硬解码h265视频，我是参考[这篇教程](https://github.com/JavaNoober/MedioDecode)，然后项目有了一个新的需求，要解码没有通过封装的视频（非.mp4格式），就需要我提取h265的一些数据，独立喂给mediacodec的解码器。

对h265格式的视频进行分析，能够发现，





