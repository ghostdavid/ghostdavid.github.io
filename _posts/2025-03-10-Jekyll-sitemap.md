---
title: Jekyll自动生成站点地图并提交Google & Bing搜索引擎收录
date: 2025-03-11 0:00:00 +0800
categories: [Build Website]
tags: [jekyll,website,sitemap,google,bing]
---

以我的网站为例，采用的是jekyll+github page托管的方式建站



## 1、修改Gemfile文件

在github项目的根目录找到Gemfile文件

![](https://tuchuang.ghostdavid.top/20250310231924725.png)

打开后，在最后直接加上`gem 'jekyll-sitemap'`，保存提交即可

![](https://tuchuang.ghostdavid.top/20250310232922869.png)	

## 2、修改_config.yml文件

在根目录找到_config.yml文件

![](https://tuchuang.ghostdavid.top/20250310233607864.png)

加一行如下语句，加在哪里都行，我是加在了url的下面，保存提交即可

```
plugins:
  - jekyll-sitemap
```

![](https://tuchuang.ghostdavid.top/20250311003711260.png)

## 3、检查sitemap页面

网站打包完成后，直接在浏览器地址栏输入`https://你的域名/sitemap.xml`，这个页面只能输入网址去看，项目目录里是没有的。以我的网站为例，就是 https://ghostdavid.github.io/sitemap.xml

正常的话应该是如下这样：

![](https://tuchuang.ghostdavid.top/20250310234250491.png)

## 4、Google Search Console收录

网站：https://search.google.com/search-console/about

如果是你自己的域名，就填左边的网域。如果是example.github.io，就填右边的网址前缀

所有权验证主要有三种方式，一种是在根目录上传html文件验证，另一种是在html网页中加入标记代码，还有一种是通过DNS服务商验证。只要能确保验证方式长期稳定，那么哪种都行

![](https://tuchuang.ghostdavid.top/20250310234748888.png)

验证通过后，在网站地图中加入前面获得的sitemap网址，然后就是慢慢等待谷歌爬虫即可

![](https://tuchuang.ghostdavid.top/20250311001927629.png)

![](https://tuchuang.ghostdavid.top/20250311002327925.png)

## 5、Bing Webmaster Tools收录

网站：https://www.bing.com/webmasters/home

可以从Google导入，或是直接网址添加

网站地图也是同样方式提交

![](https://tuchuang.ghostdavid.top/20250311002721472.png)

![](https://tuchuang.ghostdavid.top/20250311002851299.png)

## 参考资料：

https://github.com/jekyll/jekyll-sitemap
