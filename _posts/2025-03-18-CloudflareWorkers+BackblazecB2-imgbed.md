---
layout: post
title: Cloudflare Workers+Backblazec B2私密桶建立无限制图床
date: 2025-03-18 11:00:00 +0800
categories: [Build Website]
tags: [cloudflare,imgbed,backblazec]
---



## 详细教程见这篇文章

[https://blog.standat42.com/posts/image-hosting-backblaze-b2-private-cloudflare-workers-picgo](https://blog.standat42.com/posts/image-hosting-backblaze-b2-private-cloudflare-workers-picgo)

这位作者将过程写的非常清楚，我按他的教程做了一遍，流程没问题，跑的通，这边我简单说一下优缺点

**这个方案本质上是在Backblazec上建立一个存储桶，然后将这个存储桶通过Cloudflare Workers挂靠到Cloudflare的域名上，实现无限流量、无限空间**

如果你想流畅使用，你需要：

- 一个Cloudflare账户
- 一个Backblazec账户
- 一个自己的域名（若不在中国大陆使用，则可选）


## 相比于单纯的Cloudflare R2存储桶
优点

- 无限制：虽然Backblazec存储桶自身是有限制的，但因为Cloudflare和Backblazec同属带宽联盟，两者之间的流量免费。所以通过Cloudflare域名访问Backblaze存储的图片不计流量费，间接实现无限流量
- 不需要绑定付款方式：Backblazec公开桶现在被要求必须绑定付款方式，但私密桶目前（2025.03）不需要

缺点

- 如果你有自己的域名，这就不是缺点。如果你没有，理论上是可以用Cloudflare的workers.dev子域，但可惜这个子域在中国大陆是被墙的，无法使用和访问


## 针对缺点，可能的解决方式
后来想到的一个办法是，使用Webp Cloud服务对workers.dev子域进行代理转换，然后使用Webp Cloud提供的域名作为图床url域名。

虽然Webp Cloud是个开源服务，也有一定免费额度，但额度不高，而且是小团队做的，可持续性需自行评估。后续我会针对这个Webp Cloud服务写一篇文章
