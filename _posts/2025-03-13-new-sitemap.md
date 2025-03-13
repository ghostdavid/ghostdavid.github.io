---
layout: post
title: 自定义程度更高的sitemap生成方式，适合多个域名
date: 2025-03-13 14:00:00 +0800
categories: [Build Website]
tags: [jekyll,website,sitemap]
---

我的另一篇文章中(https://ghostdavid.pages.dev/posts/Jekyll-sitemap) 有介绍以jekyll插件的方式建立sitemap，但那个方式只能建立单个域名的sitemap，无法自定义额外参数，也无法生成在根目录可见的xml文件。所以我在网上搜索后，发现了一个更方便的sitemap生成方式

## 设置url

我的网站有三个域名，我想制作每个域名所对应的网站地图，所以在_config.yml中要设置好三个url变量值，

``` yml
url_github: "https://ghostdavid.github.io"
url_cloudflare: "https://ghostdavid.pages.dev"
url_personal: "https://ghostdavid.top"
```
## 新建sitemap-xxx.xml

在项目根目录新建三个sitemap-xxx.xml文件，内容如下（这里以sitemap-github.xml举例），不同sitemap文件只需更改文件名和文件中的`site.url`的后缀即可

``` xml
{% raw %}    
---
layout: null
sitemap:
  exclude: 'yes'
---

<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
  {% for post in site.posts %}
    {% unless post.published == false %}
    <url>
      <loc>{{ site.url_github }}{{ post.url }}</loc>
      <lastmod>{{ post.date | date_to_xmlschema }}</lastmod>
    </url>
    {% endunless %}
  {% endfor %}
  {% for page in site.pages %}
    {% unless page.sitemap.exclude == "yes" %}
    <url>
      <loc>{{ site.url_github }}{{ page.url | remove: "index.html" }}</loc>
    </url>
    {% endunless %}
  {% endfor %}
</urlset>
{% endraw %}  
```

## 自定义参数
除了<loc>和<lastmod>，还可以增加如下两种参数：
- <changefreq>monthly</changefreq>
- <priority>0.5</priority>

loc 代表网页的网址

lastmod 代表最后修改日期

changefreq 代表网页可能变更的频率，有效值如下：

- always
- hourly
- daily
- weekly
- monthly
- yearly
- never

priority 代表此网址相对于您网站上的其他网址的优先级，有效值从 0.0 到 1.0



## 保存提交

等待部署完成，就能生成不同域名的sitemap地址，比如我的网站站点地图：

- https://ghostdavid.github.io/sitemap-github.xml
- https://ghostdavid.pages.dev/sitemap-cloudflare.xml
- https://ghostdavid.top/sitemap-personal.xml

将以上地址分别提交至Bing和Google对应域名下的站点地图即可



## 参考资料

https://blog.poychang.net/generating-sitemap-in-jekyll-without-plugin/

https://blog.17study.com.cn/2017/12/29/sitemap_of_jekyll/
