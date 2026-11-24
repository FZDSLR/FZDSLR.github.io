---
title: 解决无法连接部署在 Vercel 上的 Waline 服务的问题
categories:
 - 技术
tags: 
 - 技术
 - Hexo
cover: https://cdn1.fzdslr.cn/Pic/Tec/waline-vercel.jpg
date: 2022-10-02 20:30:00
---

## 起因

前几天翻博客的时候发现自己博客底下的评论加载不出来，经过排查，最终确定是因为 `vercel.app` <s>因为某种神秘的力量而</s>无法访问，导致 Waline 前端无法连接部署在 `vercel` 上的服务端。

## 解决方法

这个问题的解决思路很明确：既然 `vercel.app` 用不了，那就用另一个域名替代掉就行。我的解决方法是使用一个二级域名分配给部署在 Vercel 上的服务端，然后在 Hexo 的配置文件里更改服务端网址。

### DNS 配置

在自己的域名的 DNS 配置界面新增一条 `CNAME` 记录，指向 `cname.vercel-dns.com`。

### Vercel 配置

在 `Settings-Domains` 添加之前设定的二级域名。

### Hexo 配置

以我目前使用的 Butterfly 主题为例，在 `_config.butterfly.yml` 中修改

```
 waline:
   serverURL: https://xxxx.xxx.xx # Waline server address url
```

为之前设定的二级域名。

然后重新生成静态页面并部署即可。
