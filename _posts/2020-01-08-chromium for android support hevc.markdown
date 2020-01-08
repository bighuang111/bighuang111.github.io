---
layout:     post
title:      "chromium for android support hevc"
subtitle:   "每天都要变博学的小黄"
date:       2020-01-08 19:11:00
author:     "LittleHuang"
header-img: "img/in-post/post-eleme-pwa/eleme-at-io.jpg"
header-mask: 0.3
catalog:    true
tags:
    - chromium
    - android
typora-root-url: ..\img\root-samsung
---

# Chromium for android support hevc

#### 根据官方教程步骤下载源文件

Checking out and building Chromium for Android

https://chromium.googlesource.com/chromium/src/+/master/docs/android_build_instructions.md

Checking out and building Chromium on Linux

https://chromium.googlesource.com/chromium/src/+/master/docs/linux_build_instructions.md#Run-Chromium

GN-build-configuration

https://www.chromium.org/developers/gn-build-configuration

GN命令详情

https://gn.googlesource.com/gn/+/master/docs/reference.md#cmd_gen

遇到问题；

1.gclient sync中设置代理

使用命令：

export NO_AUTH_BOTO_CONFIG=/home/ngs/.boto

echo -e "[Boto]\nproxy=child-prc.intel.com\nproxy_port=913">/home/ngs/.boto

参考文档：ywnz.com/linuxjc/2405.html

2.遇到 pkgresult=exec_script(pkg_config_script,args,"value")

apt-get install pkg-config

3.需要javap指令，即安装jdk



#### 导出支持h265的安卓端apk

[参考链接](https://segmentfault.com/a/1190000020711813)

1.修改`src/third_party/ffmpeg/ffmpeg_generated.gni`这个文件

加入一下代码

```
if ((is_mac) || (is_win) || (use_linux_config)) {
  ffmpeg_c_sources += [
    "libavcodec/autorename_libavcodec_hpeldsp.c",
    "libavcodec/autorename_libavcodec_videodsp.c",
    "libavcodec/autorename_libavcodec_vp3dsp.c",
    "libavcodec/autorename_libavcodec_vp8dsp.c",
    "libavcodec/h264pred.c",
    "libavcodec/vp3.c",
    "libavcodec/vp3_parser.c",
    "libavcodec/vp56rac.c",
    "libavcodec/vp8.c",
    "libavcodec/vp8_parser.c",
  ]

  ffmpeg_c_sources += [
    "libavcodec/bswapdsp.c",
    "libavcodec/autorename_libavcodec_hevcdec.c",
    "libavcodec/hevc_cabac.c",
    "libavcodec/hevc_data.c",
    "libavcodec/hevc_filter.c",
    "libavcodec/hevc_mvs.c",
    "libavcodec/hevc_parse.c",
    "libavcodec/hevc_parser.c",
    "libavcodec/hevc_ps.c",
    "libavcodec/hevc_refs.c",
    "libavcodec/hevc_sei.c",
    "libavcodec/hevcdsp.c",
    "libavcodec/hevcpred.c",
    "libavcodec/x86/bswapdsp_init.c",
    "libavcodec/x86/hevcdsp_init.c",
    "libavformat/autorename_libavformat_hevc.c",
    "libavformat/hevcdec.c",
  ]
  ffmpeg_asm_sources += [
    "libavcodec/x86/bswapdsp.asm",
    "libavcodec/x86/hevc_deblock.asm",
    "libavcodec/x86/hevc_idct.asm",
    "libavcodec/x86/hevc_mc.asm",
    "libavcodec/x86/hevc_add_res.asm",
    "libavcodec/x86/hevc_sao.asm",
    "libavcodec/x86/hevc_sao_10bit.asm",
  ]
}
```

2.复制并重命名这个文件里面的两个文件`src/third_party/ffmpeg`

`libavcodec/hevcdec.c` to `libavcodec/autorename_libavcodec_hevcdec.c`

`libavformat/hevc.c`to `libavformat/autorename_libavformat_hevc.c`

3.修改`src/third_party/ffmpeg/chromium/conifg/Chrome/linux/arm64/config.h`文件

将下面的几个值改成 1 

```
#define CONFIG_HEVC_DECODER 1
#define CONFIG_HEVC_DEMUXER 1
#define CONFIG_HEVC_PARSER 1
```

4.在`src/third_party/ffmpeg/chromium/conifg/Chrome/linux/arm64/libavcodec/codec_list.c`中添加一行`&ff_hevc_decoder`

`src/third_party/ffmpeg/chromium/conifg/Chrome/linux/arm64/libavcodec/parser_list.c`中添加一行`&ff_hevc_parser`

`src/third_party/ffmpeg/chromium/conifg/Chrome/linux/arm64/libavformat/demuxer_list.c`中添加一行`&ff_hevc_demuxer`

5.修改文件`src/media/base/supported_types.cc`

```
bool IsDefaultSupportedVideoType(const VideoType& type) {
//...
switch (type.codec) {
    // ....
    case kCodecH264:
  + case kCodecHEVC:
    case kCodecVP8:
    case kCodecTheora:
        return true;

    case kUnknownVideoCodec:
    case kCodecVC1:
    case kCodecMPEG2:
  - case kCodecHEVC:
    case kCodecDolbyVision:
        return false;
    // ...
}
```

修改文件`src/media/media_options.gni`

```
- enable_platform_hevc = proprietary_codecs && is_chromecast
+ enable_platform_hevc = true
```

6.在src目录下执行`gn args out/Default`,然后用一下参数编辑文件：

```
target_os = "android"
target_cpu = "arm64"
ffmpeg_branding = "Chrome" 
proprietary_codecs = true
```

执行`autoninja -C out/Default chrome_public_apk`生成apk文件

`gn args --list out/Default`列出当前使用的所有参数

7.安装应用

执行`third_party/android_sdk/public/platform-tools/adb devices`，将会打印已经链接上的设备，如果没有显示，看看开发者模式中的USB调试是否打开。

`third_party/android_sdk/public/platform-tools/adb shell settings put global verifier_verify_adb_installs 0 `,将允许安卓设备安装未知应用。

`adb install path/to/.apk`安装应用

8.测试

测试网址是`59.110.159.130:2013`























