---
title: Jekyll更改网站图标
date: 2025-03-11 1:00:00 +0800
categories: [Build Website]
tags: [jekyll,website,icon]
---

以我的网站为例，采用的是jekyll+github page托管的方式建站

## 创建图标目录

在项目根目录创建`assets/img/favicons/`文件夹

![20250311005355172](https://github.com/user-attachments/assets/8d3f6b26-5631-4db8-bb38-426f35cd29c4)

## 生成图标素材

打开网站：https://realfavicongenerator.net/

上传你的图标

![20250311005449008](https://github.com/user-attachments/assets/96a531e1-ca83-45ee-8654-28e3e01dec4c)

上传后可以自定义样式，也可以默认什么都不改，直接拉到最后点击next

![20250311005343152](https://github.com/user-attachments/assets/39a138cb-144a-4ccc-a0cd-b9729c46eb9e)

直接下载压缩包

![20250311005615474](https://github.com/user-attachments/assets/3c2d9621-b4a7-4d8f-af23-f06e9a999eeb)

## 上传图标素材至项目目录

压缩包解压后，删除site.webmanifest和browserconfig.xml文件，然后把剩余所以文件上传至项目的assets/img/favicons/文件夹，最后等待网站刷新即可

![20250311005925451](https://github.com/user-attachments/assets/1364ff2f-44bf-4063-8eaf-8e16482be233)




## 参考资料：

https://chirpy.cotes.page/posts/customize-the-favicon/




