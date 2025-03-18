---
layout: post
title: 如何关闭Windows自带虚拟机服务Hyper-V？
date: 2025-03-19 00:30:00 +0800
categories: [Windows,System]
tags: [windows,Hyper-V]
---

注：由于文章最初发表于CSDN账号，所以转移过来后图片留有水印

## 目的
在BIOS里已经开启虚拟化的情况下，解决第三方虚拟机软件，比如VMware Workstation Pro，提示CPU未开启虚拟化，无法创建虚拟机的问题

## 打开Windows Powershell

![73bf0771f19a4bd29bf16653dc98a274.png](/2025/03/1742315298145_73bf0771f19a4bd29bf16653dc98a274.png)

##  关闭Hyper-V服务

 输入命令行`bcdedit /set hypervisorlaunchtype off`

 ![223e78ac05a44e249c304ac26534f152.png](/2025/03/1742315306890_223e78ac05a44e249c304ac26534f152.png)

 然后重启电脑生效

## 如果要恢复Hyper-V服务

 输入命令行`bcdedit / set hypervisorlaunchtype auto`

