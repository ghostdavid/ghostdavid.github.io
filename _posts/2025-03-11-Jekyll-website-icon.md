---
title: Jekyll更改网站图标
date: 2025-03-11 1:00:00 +0800
categories: [Build Website]
tags: [jekyll,website,icon]
---

以我的网站为例，采用的是jekyll+github page托管的方式建站

## 创建图标目录

在项目根目录创建`assets/img/favicons/`文件夹

![](https://pub-05bbf0f9a3e14287a8e9eafbc6a26a1f.r2.dev/20250311005355172.png)

## 生成图标素材

打开网站：https://realfavicongenerator.net/

上传你的图标

![](https://pub-05bbf0f9a3e14287a8e9eafbc6a26a1f.r2.dev/20250311005449008.png)

上传后可以自定义样式，也可以默认什么都不改，直接拉到最后点击next

![](https://pub-05bbf0f9a3e14287a8e9eafbc6a26a1f.r2.dev/20250311005343152.png)

直接下载压缩包

![](https://pub-05bbf0f9a3e14287a8e9eafbc6a26a1f.r2.dev/20250311005615474.png)

## 上传图标素材至项目目录

压缩包解压后，删除site.webmanifest和browserconfig.xml文件，然后把剩余所以文件上传至项目的assets/img/favicons/文件夹，最后等待网站刷新即可

![](https://pub-05bbf0f9a3e14287a8e9eafbc6a26a1f.r2.dev/20250311005925451.png)







## 参考资料：

https://chirpy.cotes.page/posts/customize-the-favicon/



