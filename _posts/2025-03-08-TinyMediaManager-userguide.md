---
title: TinyMediaManager配置指南
date: 2025-03-08 1:00:00 +0800
categories: [NAS,Docker]
tags: [nas,docker,tv,movie]
---

一些不重要的设置，本文不做展示和介绍，操作时直接下一步or跳过or默认配置即可

## 1、什么是TinyMediaManager？

常用的NAS媒体库软件有Jellyfin、Emby、Plex、Kodi等等，但它们的内置刮削器有时候并不太好用，我这边推荐使用TinyMediaManager作为刮削器、媒体文件管理平台使用，而Jellyfin等媒体库软件仅作为媒体读取、播放、展示的平台。TinyMediaManager除了有Windows、Mac客户端，还有docker版本，本文展示的是docker版本的配置和使用

### 刮削后在Jellyfin中展示

海报墙

![20250308025024420](https://github.com/user-attachments/assets/99dbc683-ec5c-4a89-9e6f-6f23a5177569)

电视剧

![20250308025519572](https://github.com/user-attachments/assets/2087a76d-5cfd-49c9-93a6-08129d71911a)

剧集

![20250308025519574](https://github.com/user-attachments/assets/3dc8ea69-85d1-40a7-9d5d-053949286f39)

### 刮削后文件夹系统展示

电视剧文件夹



![20250308025519575](https://github.com/user-attachments/assets/fe98a1d3-877b-4462-bc1c-5aa9b4201b65)

季文件夹



![20250308025519576](https://github.com/user-attachments/assets/094c4aa8-e39b-40db-880e-98ef638f9ce6)

剧集、nfo、缩略图

中文字幕建议软件外自行下载重命名



![20250308025519577](https://github.com/user-attachments/assets/1c1b5a01-2ec7-4c05-8b57-3de0bc030474)

------

## 2、容器下载和配置

### 镜像仓库搜索dzhuang/tinymediamanager

这个镜像是专门对中文做了字体优化，避免了UI出现乱码方块字

![20250308025519578](https://github.com/user-attachments/assets/97134b1f-fd4e-41b4-8037-42cd86cb6044)

### 下载latest或v3.1.16版本

因为v3.1.16是最后的全功能免费版本，v4以上版本部分功能需要付费才能使用



![20250308025519579](https://github.com/user-attachments/assets/b2abf094-cbf9-4a8e-be87-ffdf2b121c67)

### 创建容器

镜像下载完成后，点击创建容器，容器名称自定



![20250308025519580](https://github.com/user-attachments/assets/636785d7-0b28-4807-8849-7780a17ef0d5)



### 重启策略



![20250308025519581](https://github.com/user-attachments/assets/8c9ff419-e73c-4181-99a6-512585228511)



### 存储空间

自行设置目录，并设为读写权限。建议电影和电视剧分两个文件夹



![20250308025519582](https://github.com/user-attachments/assets/1dd831d1-1e48-462b-9606-927fe43d66bb)


### 端口

默认自动或自定，不与其他容器端口冲突即可



![20250308025519583](https://github.com/user-attachments/assets/36ce1385-cd02-420a-ab12-0b9c8c01a216)



### 环境变量

1. USER_ID和GROUP_ID通常不需要更改，如果后续发现容器无法移动文件，可以改为0
2. display_width和display_height可以修改UI分辨率



![20250308025519584](https://github.com/user-attachments/assets/e1a50730-5b9c-4331-a1a6-94c61b742e70)



![20250308025519585](https://github.com/user-attachments/assets/223af9bd-d725-4d63-93e5-de03fbb8f2a5)

------

## 3、TinyMediaManager设置向导

### 更新弹窗

TinyMediaManager每次启动都会提示更新，直接关闭即可。点更新会卡死，需要重启容器



![20250308025519586](https://github.com/user-attachments/assets/cd13cfe7-9706-4a0b-88f9-ff4b1edd388a)

### 语言设置

下拉选择中文，重启容器生效，可以向导走完再重启



![20250308025519587](https://github.com/user-attachments/assets/366b4845-6c21-4817-bcf5-96953ce9d71e)

### 电影、电视剧源设置

1. 选择各自的电影、电视文件夹
2. 刮削器设置themoviedb
3. 刮削语言设置大陆简体
4. 勾选成人内容、刮削语言名/国家名、使用后备语言抓取标题



![20250308025519588](https://github.com/user-attachments/assets/adcaaaca-221c-4383-a140-fee7c9b85c30)



![20250308025519589](https://github.com/user-attachments/assets/6cf0a103-7460-4c5c-8131-81c4052a6f69)



![20250308025519590](https://github.com/user-attachments/assets/67e388c8-9550-4867-ac6e-eed6e0461129)

### 重启容器



![20250308025519591](https://github.com/user-attachments/assets/ecd60fdc-5b19-4a0d-bb86-1f46953148b0)

------

## 4、通用选项推荐设置

### 通用选项



![20250308025519592](https://github.com/user-attachments/assets/c54afbbf-6f92-455a-a13f-aecfb334209a)



### 系统

1. 内存建议给足
2. 如果你有自己的代理服务器，在这里填，用于”加速“刮削
3. 并行下载数可以填大一点



![20250308025519593](https://github.com/user-attachments/assets/265eb17c-1538-4975-919c-21b0e158440b)



### 杂项

取消勾选图片快取可以加快载入

![20250308025519594](https://github.com/user-attachments/assets/bd2a2e46-f882-451c-9930-dc6eae1ca360)



## 5、电视剧刮削推荐设置

电影和电视剧类似，就不做阐述，可自行研究

### 电视节目

自动重命名建议打开，后面有相关规则推荐设置



![20250308025519595](https://github.com/user-attachments/assets/c2592b8f-dbdd-4e09-8d76-6701586478f1)



### 刮削器



![20250308025519596](https://github.com/user-attachments/assets/79afd6cc-fbed-40a2-b98c-2ca84412c6e4)



### 刮削器选项



![20250308025519597](https://github.com/user-attachments/assets/25b18b54-3f63-4965-834e-b5d9acf5178b)



### NFO设置



![20250308025519598](https://github.com/user-attachments/assets/a7012f3a-60a3-4227-87ae-f5d9ef8df064)



### 图片



![20250308025519599](https://github.com/user-attachments/assets/0ec52bb9-b7bc-4964-8a2d-32fe9b278169)



### 剧照档案名



![20250308025519600](https://github.com/user-attachments/assets/d8d01adc-494e-4c4a-9ea5-49a4df23a52d)



### 重命名规则

1. 电视剧文件夹建议设为${showTitle} ${showoriginalTitle} (${showYear})
2. 季文件夹建议设为Season ${seasonNr2}
3. 剧集名建议空着，不建议重命名视频文件



![20250308025519601](https://github.com/user-attachments/assets/3ba9603a-573d-4733-ac17-c4e6ee4ff77a)



## 6、刮削

### 初步分类

电视剧先手动按文件夹做个初步的分类，比如一个电视剧一个文件夹，所有剧集都放里面即可，文件夹内不必再按季分类

### 更新数据源

媒体文件夹如果有加入新文件，软件需要更新数据源，否则不会刷新增加的文件



![20250308025519602](https://github.com/user-attachments/assets/ec711c12-101f-4da1-8da0-7f53a0b5e6f4)



### 搜索并刮削

右键点击初步分类出的剧集文件夹，选择 搜索并刮削已选电视节目



![20250308025519603](https://github.com/user-attachments/assets/6b04233a-1346-412d-b438-a73fe5f7977a)



检查是否识别正确，如果有误，选择正确结果或修改搜索关键词



![20250308025519604](https://github.com/user-attachments/assets/29f921da-ed0b-4846-87e2-d7e195322c1e)



点击确定，等待刮削完成。软件会按季自动建文件夹，自动完成重命名操作



![20250308025519605](https://github.com/user-attachments/assets/5c692d8d-4c4e-49b5-b8a1-193f966af1e0)
