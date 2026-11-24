---
title: 使用自己的域名访问 Github 上的资源
categories:
 - Hexo
tags: 
 - 技术
 - Hexo
cover: https://cdn1.fzdslr.cn/Pic/cover/wp2258508-1.jpg
date: 2021-09-12 12:00:00
---

# 前言

在此之前，我为了解决博客图片的访问问题，采用的方案是：

- 把 Github 当图床
- 使用 `cdn.jsdelivr.net`提供的加速服务

但这存在几点问题：

- 严格来说，以上的做法属于滥用行为，存在一定风险
- 如果日后想要迁移服务，那么博客图片的域名更改将成为一个大问题

恰好，我前一段时间购买了`fzdslr.cn`这个域名，于是我利用 Github Pages 服务，成功使用`cdn1.fzdslr.cn`访问了我存在 Github 上的图片。



# 域名部分

进入域名解析界面，添加一条主机记录作为二级域名（以`cdn1`为例），记录类型为`CNAME`，记录值指向`(用户名).github.io`。

# Github 部分

新建一个公共仓库（以`PicCDNTest`为例），新建一个`index.html`文件和一个`CNAME`文件，在`CNAME`文件中填写之前完成解析的域名（如`cdn1.fzdslr.cn`）。然后进入`settings`-`pages`，打开 Github Pages 服务。



然后就可以使用 Picgo 上传图片了。

