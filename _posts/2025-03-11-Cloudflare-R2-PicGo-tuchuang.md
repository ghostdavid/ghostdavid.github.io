---
layout: post
title: Cloudflare R2存储+PicGo免费建立在线图床
date: 2025-03-11 2:00:00 +0800
categories: [Build Website]
tags: [cloudflare,website,picgo]
---

域名注册和托管本文不详述

如果想要畅快使用R2存储桶，需要：

- 一个域名
- 一张国际信用卡或paypal账户

## Cloudflare创建R2存储桶

R2存储桶的免费额度对于个人网站来说完全够用，但开通流程要绑定信用卡或paypal，需自行想办法解决

新建一个存储桶，名称自定义，位置选择APAC亚太

![](https://imgbed-gd.pages.dev/file/2025/03/20250311011306559.png)

![](https://imgbed-gd.pages.dev/file/2025/03/20250311011336104.png)

## R2存储桶设置

如果有自己的个人域名，可以添加自定义域。如果没有，则可以启用R2.dev子域访问，Cloudflare会提供一个域名作为文件的公开链接

![](https://imgbed-gd.pages.dev/file/2025/03/20250311013006923.png)

设置好域名后就可以直接上传文件了，打开文件即可看到公开的URL地址

![](https://imgbed-gd.pages.dev/file/2025/03/20250311014417492.png)

## 创建R2 API令牌

如图创建API令牌

![](https://imgbed-gd.pages.dev/file/2025/03/20250311014702751.png)

![](https://imgbed-gd.pages.dev/file/2025/03/20250311014807238.png)

创建后的页面记录下`访问密钥ID`、`机密访问密钥`和`为S3客户端使用管辖权地特定的终结点`

![](https://imgbed-gd.pages.dev/file/2025/03/20250311015001864.png)

## PicGo及插件安装

PicGo下载地址：https://github.com/Molunerfinn/PicGo

插件建议安装S3-lls, compress, remove-exif这三款插件 （插件安装会需要安装node.js环境，以及梯子的全局系统代理，否则会失败）

![](https://imgbed-gd.pages.dev/file/2025/03/20250311015512221.png)

S3-lls用于后续登录S3 API

compress用于压缩照片（压缩引擎建议选择本地的imagemin，详细见https://github.com/JuZiSang/picgo-plugin-compress）

remove-exif用于移除照片exif信息

![](https://imgbed-gd.pages.dev/file/2025/03/20250311015449933.png)

![](https://imgbed-gd.pages.dev/file/2025/03/20250311015817987.png)

## PicGo S3 API设置

图床设置找到Amazon S3，点击编辑

![](https://imgbed-gd.pages.dev/file/2025/03/20250311020108636.png)

应用密钥ID=API令牌的`访问密钥ID`

应用密钥=API令牌的`机密访问密钥`

桶=`R2存储桶的名字`

自定义节点=API令牌的`为S3客户端使用管辖权地特定的终结点`

自定义域名=设置R2存储桶时的`三级域名`

其他按我图片里的填或自行修改，最后保存并设为默认图床

![](https://imgbed-gd.pages.dev/file/2025/03/20250311020133897.png)

![](https://imgbed-gd.pages.dev/file/2025/03/20250311020157649.png)

## 通过PicGo上传图片并自动获取URL

PicGo设置建议开启以下两项

![](https://imgbed-gd.pages.dev/file/2025/03/20250311020849995.png)

最后就可以愉快上传图片了，上传后会自动复制图片URL，方便在markdown编辑器里粘贴，相册页也会展示所有上传的图片

![](https://imgbed-gd.pages.dev/file/2025/03/20250311020741613.png)
