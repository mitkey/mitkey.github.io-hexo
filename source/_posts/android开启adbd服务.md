---
title: android开启adbd服务
tags:
  - Dev
  - Commond
categories:
  - Android
comments: false
date: 2019-04-27 16:39:03
updated: 2019-04-27 16:39:03
password:
---

目前有一需求，需要在 pc 使用 adb 命令连接手机（在同一局域网内）。
当使用 adb connect 192.168.1.xxx 连接 android 设备无法成功时，往往是因为未开启 adbd 服务。

<!-- more -->

## 命令修改

	// 超级权限 
	su

	// 停用安全选项
	setprop ro.secure 0
	
	// 查看安全选项 ---> 1 为成功
	getprop ro.secure 0
	
	// adb 默认为激活状态
	setprop persist.service.adb.enable 1
	
	// 设置 adb 端口为 5555
	setprop service.adb.tcp.port 5555
	
	// 停止与开启
	stop adbd
	start adbd
	
## 文件修改

	修改 build.prop 文件(位于 /system/build.prop)
	
	在文件后面追加
	
		ro.secure 0
		persist.service.adb.enable 1	
		service.adb.tcp.port 5555
		
	重启手机，有时重启也不会加载 build.prop。最好是关机后在开机
	

## adb 帮助文档
	http://developer.android.com/tools/help/adb.html (需要翻墙)