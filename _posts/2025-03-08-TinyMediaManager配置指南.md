---
title: TinyMediaManager配置指南
date: 2025-03-08 1:00:00 +0800
categories: [NAS,docker]
tags: [NAS,docker,影视,刮削]
---

一些不重要的设置，本文不做展示和介绍，操作时直接下一步or跳过or默认配置即可

## 1、什么是TinyMediaManager？

常用的NAS媒体库软件有Jellyfin、Emby、Plex、Kodi等等，但它们的内置刮削器有时候并不太好用，我这边推荐使用TinyMediaManager作为刮削器、媒体文件管理平台使用，而Jellyfin等媒体库软件仅作为媒体读取、播放、展示的平台。TinyMediaManager除了有Windows、Mac客户端，还有docker版本，本文展示的是docker版本的配置和使用

### 刮削后在Jellyfin中展示

海报墙

![](https://tuchuang.ghostdavid.top/20250308025024420.png)

电视剧

![](https://tuchuang.ghostdavid.top/20250308025519572.png)

剧集

![](https://tuchuang.ghostdavid.top/20250308025519574.png)

### 刮削后文件夹系统展示

电视剧文件夹



![](https://tuchuang.ghostdavid.top/20250308025519575.png)

季文件夹



![](https://tuchuang.ghostdavid.top/20250308025519576.png)

剧集、nfo、缩略图

中文字幕建议软件外自行下载重命名



![](https://tuchuang.ghostdavid.top/20250308025519577.png)

------

## 2、容器下载和配置

### 镜像仓库搜索dzhuang/tinymediamanager

这个镜像是专门对中文做了字体优化，避免了UI出现乱码方块字

![](https://tuchuang.ghostdavid.top/20250308025519578.png)

### 下载latest或v3.1.16版本

因为v3.1.16是最后的全功能免费版本，v4以上版本部分功能需要付费才能使用



![](https://tuchuang.ghostdavid.top/20250308025519579.png)

### 创建容器

镜像下载完成后，点击创建容器，容器名称自定



![](https://tuchuang.ghostdavid.top/20250308025519580.png)



### 重启策略



![](https://tuchuang.ghostdavid.top/20250308025519581.png)



### 存储空间

自行设置目录，并设为读写权限。建议电影和电视剧分两个文件夹



![](https://tuchuang.ghostdavid.top/20250308025519582.png)


### 端口

默认自动或自定，不与其他容器端口冲突即可



![](https://tuchuang.ghostdavid.top/20250308025519583.png)



### 环境变量

1. USER_ID和GROUP_ID通常不需要更改，如果后续发现容器无法移动文件，可以改为0
2. display_width和display_height可以修改UI分辨率



![](https://tuchuang.ghostdavid.top/20250308025519584.png)



![](https://tuchuang.ghostdavid.top/20250308025519585.png)

------

## 3、TinyMediaManager设置向导

### 更新弹窗

TinyMediaManager每次启动都会提示更新，直接关闭即可。点更新会卡死，需要重启容器



![](https://tuchuang.ghostdavid.top/20250308025519586.png)

### 语言设置

下拉选择中文，重启容器生效，可以向导走完再重启



![](https://tuchuang.ghostdavid.top/20250308025519587.png)

### 电影、电视剧源设置

1. 选择各自的电影、电视文件夹
2. 刮削器设置themoviedb
3. 刮削语言设置大陆简体
4. 勾选成人内容、刮削语言名/国家名、使用后备语言抓取标题



![](https://tuchuang.ghostdavid.top/20250308025519588.png)



![](https://tuchuang.ghostdavid.top/20250308025519589.png)



![](https://tuchuang.ghostdavid.top/20250308025519590.png)

### 重启容器



![](https://tuchuang.ghostdavid.top/20250308025519591.png)

------

## 4、通用选项推荐设置

### 通用选项



![](https://tuchuang.ghostdavid.top/20250308025519592.png)



### 系统

1. 内存建议给足
2. 如果你有自己的代理服务器，在这里填，用于”加速“刮削
3. 并行下载数可以填大一点



![](https://tuchuang.ghostdavid.top/20250308025519593.png)



### 杂项

取消勾选图片快取可以加快载入

![](https://tuchuang.ghostdavid.top/20250308025519594.png)



## 5、电视剧刮削推荐设置

电影和电视剧类似，就不做阐述，可自行研究

### 电视节目

自动重命名建议打开，后面有相关规则推荐设置



![](https://tuchuang.ghostdavid.top/20250308025519595.png)



### 刮削器



![](https://tuchuang.ghostdavid.top/20250308025519596.png)



### 刮削器选项



![](https://tuchuang.ghostdavid.top/20250308025519597.png)



### NFO设置



![](https://tuchuang.ghostdavid.top/20250308025519598.png)



### 图片



![](https://tuchuang.ghostdavid.top/20250308025519599.png)



### 剧照档案名



![](https://tuchuang.ghostdavid.top/20250308025519600.png)



### 重命名规则

1. 电视剧文件夹建议设为${showTitle} ${showoriginalTitle} (${showYear})
2. 季文件夹建议设为Season ${seasonNr2}
3. 剧集名建议空着，不建议重命名视频文件



![](https://tuchuang.ghostdavid.top/20250308025519601.png)



## 6、刮削

### 初步分类

电视剧先手动按文件夹做个初步的分类，比如一个电视剧一个文件夹，所有剧集都放里面即可，文件夹内不必再按季分类

### 更新数据源

媒体文件夹如果有加入新文件，软件需要更新数据源，否则不会刷新增加的文件



![](https://tuchuang.ghostdavid.top/20250308025519602.png)



### 搜索并刮削

右键点击初步分类出的剧集文件夹，选择 搜索并刮削已选电视节目



![](https://tuchuang.ghostdavid.top/20250308025519603.png)



检查是否识别正确，如果有误，选择正确结果或修改搜索关键词



![](https://tuchuang.ghostdavid.top/20250308025519604.png)



点击确定，等待刮削完成。软件会按季自动建文件夹，自动完成重命名操作



![](https://tuchuang.ghostdavid.top/20250308025519605.png)
