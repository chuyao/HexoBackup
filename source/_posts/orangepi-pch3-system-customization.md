---
title: OrangePi-PCH3安卓系统定制
tags: Android
categories: Tech
date: 2018-01-07 15:09:45
---

#### 一、USB调试开放
1、修改USB0配置 /lichee/tools/pack/chips/sun8iw7p1/configs/dolphin-p1/sys_config.fex

[usbc0]
usb_used                = 1
usb_port_type         = 0    // 0:device only; 1:host only; 2:OTG，默认是1
usb_detect_type     = 0

2、重复lichee编译
3、pack

#### 二、网络调试开放
android/device/softwinner/dophin-common/init.sun8i.rc添加
on boot
setprop service.adb.tcp.port 5555
stop adbd
start adbd

#### 三、精简系统应用
1、android/vendor/fvd/fvd.mk(对应的特殊版本定制的应用)修改
      android/build/target/product/tvd_base.mk(基础版本应用)
      PRODUCT_PACKAGE += \
2、android/vendor/fvd/packages/
      检查各项目下Android.mk文件中的LOCAL_OVERRIDES_PACKAGES值是否覆盖了某个应用