---
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

![20250311011306559](https://github.com/user-attachments/assets/7e330f94-1c69-4863-95ee-c05cc668847b)

![20250311011336104](https://github.com/user-attachments/assets/c557fce3-819a-42cf-a39b-c67e2f61658e)

## R2存储桶设置

如果有自己的个人域名，可以添加自定义域。如果没有，则可以启用R2.dev子域访问，Cloudflare会提供一个域名作为文件的公开链接

![20250311013006923](https://github.com/user-attachments/assets/afeabb6c-c21e-4de8-a3e7-fbcd802fdf70)

设置好域名后就可以直接上传文件了，打开文件即可看到公开的URL地址

![20250311014417492](https://github.com/user-attachments/assets/aced2881-6f56-41fb-a697-acee3ba5a9bd)

## 创建R2 API令牌

如图创建API令牌

![20250311014702751](https://github.com/user-attachments/assets/e164640c-43fb-4c6d-b956-8b3e9a6c7d58)

![20250311014807238](https://github.com/user-attachments/assets/3ebf7869-5f8a-4206-8b86-5ea5555a2c12)

创建后的页面记录下`访问密钥ID`、`机密访问密钥`和`为S3客户端使用管辖权地特定的终结点`

![20250311015001864](https://github.com/user-attachments/assets/db78e14f-58f5-4069-b989-b2c69b4874bd)

## PicGo及插件安装

PicGo下载地址：https://github.com/Molunerfinn/PicGo

插件建议安装S3-lls, compress, remove-exif这三款插件 （插件安装会需要安装node.js环境，以及梯子的全局系统代理，否则会失败）

![20250311015512221](https://github.com/user-attachments/assets/97833fa5-3b86-4b96-b1c2-e18461123d92)

S3-lls用于后续登录S3 API

compress用于压缩照片（压缩引擎建议选择本地的imagemin，详细见https://github.com/JuZiSang/picgo-plugin-compress）

remove-exif用于移除照片exif信息

![20250311015449933](https://github.com/user-attachments/assets/fa33b80e-5a84-4a89-a930-da3ad81748c2)

![20250311015817987](https://github.com/user-attachments/assets/1f9936a5-d225-44bd-b12d-550a2c0ce88e)

## PicGo S3 API设置

图床设置找到Amazon S3，点击编辑

![20250311020108636](https://github.com/user-attachments/assets/e1d26c98-beea-4717-88aa-bcd15d2b44a5)

应用密钥ID=API令牌的`访问密钥ID`

应用密钥=API令牌的`机密访问密钥`

桶=`R2存储桶的名字`

自定义节点=API令牌的`为S3客户端使用管辖权地特定的终结点`

自定义域名=设置R2存储桶时的`三级域名`

其他按我图片里的填或自行修改，最后保存并设为默认图床

![20250311020133897](https://github.com/user-attachments/assets/6e26b92f-d40c-4960-b03d-5de4c315a1da)

![20250311020157649](https://github.com/user-attachments/assets/30e1fa30-7304-4e24-b41a-435e012232f4)

## 通过PicGo上传图片并自动获取URL

PicGo设置建议开启以下两项

![20250311020849995](https://github.com/user-attachments/assets/f6755eb0-c5b9-4c90-9932-023e6eafb20f)

最后就可以愉快上传图片了，上传后会自动复制图片URL，方便在markdown编辑器里粘贴，相册页也会展示所有上传的图片

![20250311020741613](https://github.com/user-attachments/assets/a2534169-abc8-4aab-be00-dcd2de53c760)
