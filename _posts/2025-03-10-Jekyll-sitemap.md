---
title: Jekyll sitemap插件生成站点地图并提交Google & Bing搜索引擎收录
date: 2025-03-11 0:00:00 +0800
categories: [Build Website]
tags: [jekyll,website,sitemap,google,bing]
---

以我的网站为例，采用的是jekyll+github page托管的方式建站

## 1、修改Gemfile文件

在github项目的根目录找到Gemfile文件

![20250310231924725](https://github.com/user-attachments/assets/203808ff-8c26-4c6e-a82e-f48f72df82b2)

打开后，在最后直接加上`gem 'jekyll-sitemap'`，保存提交即可

![20250310232922869](https://github.com/user-attachments/assets/510f900b-007b-4dea-b416-49ae3b6e7423)

## 2、修改_config.yml文件

在根目录找到_config.yml文件

![20250310233607864](https://github.com/user-attachments/assets/1a8ca678-89eb-4955-a4b9-60a2ce07dedb)

加一行如下语句，加在哪里都行，我是加在了url的下面，保存提交即可

```
plugins:
  - jekyll-sitemap
```

![20250311003711260](https://github.com/user-attachments/assets/2260587e-c573-4ad6-b3cf-b25530072062)

## 3、检查sitemap页面

网站打包完成后，直接在浏览器地址栏输入`https://你的域名/sitemap.xml`，这个页面只能输入网址去看，项目目录里是没有的

正常的话应该是如下这样：

![20250310234250491](https://github.com/user-attachments/assets/83637b11-a246-4d0e-8362-0369476c77b1)

## 4、Google Search Console收录

网站：https://search.google.com/search-console/about

如果是你自己的域名，就填左边的网域。如果是example.github.io，就填右边的网址前缀

所有权验证主要有三种方式，一种是在根目录上传html文件验证，另一种是在html网页中加入标记代码，还有一种是通过DNS服务商验证。只要能确保验证方式长期稳定，那么哪种都行

![20250310234748888](https://github.com/user-attachments/assets/635c9f1f-18b2-4ca1-92f8-33c4042c5a2e)

验证通过后，在网站地图中加入前面获得的sitemap网址，然后就是慢慢等待谷歌爬虫即可

![20250311001927629](https://github.com/user-attachments/assets/ea95c21c-f96a-4190-aef5-ba3115d04fa0)

![20250311002327925](https://github.com/user-attachments/assets/cebeddec-f6e8-408b-96dc-5c1b2a2cb03c)

## 5、Bing Webmaster Tools收录

网站：https://www.bing.com/webmasters/home

可以从Google导入，或是直接网址添加

网站地图也是同样方式提交

![20250311002721472](https://github.com/user-attachments/assets/729963c8-a7f7-4a9a-b0b0-86800b15d196)

![20250311002851299](https://github.com/user-attachments/assets/1ff4c859-21b3-4702-9bff-059d31b3f2b3)

## 参考资料：

https://github.com/jekyll/jekyll-sitemap
