---
layout: post
title: 如何开启Windows卓越性能电源模式？
date: 2025-03-19 00:15:00 +0800
categories: [Windows,System]
tags: [windows,performance,power]
---

注：由于文章最初发表于CSDN账号，所以转移过来后图片留有水印

## 目的

最大化CPU的性能释放，提升操作流畅度

但前提是硬件散热要好，比如一些散热较差的笔记本电脑开启后，反而会导致降频卡顿

## 打开Windows Powershell

![73bf0771f19a4bd29bf16653dc98a274.png](/2025/03/1742314761807_73bf0771f19a4bd29bf16653dc98a274.png)

## 启用卓越性能模式

输入命令行`powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61`，显示如下即成功

![d16682af32fb44b9b96355d6ba942318.png](/2025/03/1742314764610_d16682af32fb44b9b96355d6ba942318.png)

 在控制面板-电源选项里，就可以看到新增的卓越性能模式

![952a7a23309e42888184352c2e1980cc.png](/2025/03/1742314758839_952a7a23309e42888184352c2e1980cc.png)

