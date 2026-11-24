---
title: 黑莓Q20——RSS折腾笔记（1）
categories:
 - Blackberry
tags: 
 - 技术
 - Blackberry
 - RSS
cover: https://cdn1.fzdslr.cn/Pic/Tec/IMG_20201013_221335.jpg
date: 2020-10-17 23:00:00
---
# 前言

在国庆假期，我很不幸地发现，自己的黑莓9900的电源键坏了<span class="heimu" title="你知道的太多了">毕竟都不知道是几手机了</span>。但作为一个从三星C3222开始就使用全键盘的<span class="heimu" title="你知道的太多了">与时代脱节的（迫真）老年</span>人，又岂能容忍现在又大又薄以至于放口袋坐下时会戳到大腿的东西呢？于是我就购买了一个成色还比较新的黑莓Q20。

在之前我曾经详细地介绍过使用黑莓9900的 XPRSS 克服万难，以订阅 RSS 消息的方法。在 BB10上，这又该如何实现呢？ 

# 原生的选择：RSS Savvy

如果你在黑莓商店搜索 “RSS” ，第一个结果便是 “[RSS Savvy](https://appworld.blackberry.com/webstore/content/27344692/?lang=en&countrycode=CN)” ，这款原生的RSS订阅软件。它操作简单，运行流畅，界面简洁，的确可以满足基本的需求。

但是，作为一款 RSS 阅读器，它有着以下问题：

1. 在阅读全文 RSS 时，其体验并不算好。RSS Savvy 在其首页会显示 RSS 条目摘要的第一行，但点击 “more” 后，它并不会跳转到全文阅读页面，而是摊开摘要中的内容，然后在最下方显示`Read more...`按钮，点击后者才能进入全文阅览页面。这使得浏览全文 RSS 信息需要两步，而且是极为漫长、极易误操作的两步。

2. 阅读如微博消息时，其对多重转发后的信息兼容性极差，访问原页面时因不适配而退出阅览模式后，其阅读体验也很差。

3. 无法使用 OPML 文件批量导入 RSS 源。

4. 无法本地缓存消息，使得该阅读器依赖移动数据网络。

5. 阅览模式对图片的自适应做得很差（这也是 XPRSS 的问题之一）。

   ![](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/BB10/IMG_20201017_220811.png)

6. 使用本地访问 RSS 源的方式获取信息，鉴于天朝自有国情在此，有些 RSS 源......咳咳咳。

如果你能忍受以上所有缺点，那么 RSS Savvy 不失为一款好的 RSS 阅读器。

但问题是：

<strong>我不能忍啊！</strong>

# 寻找代替品：一次失败

众所周知，黑莓BB10系统自带一个安卓模拟机（如果你更新到了最新的模拟机版本，那么其安卓系统版本号将为4.3），这使得它可以直装一些 APK 应用程序。但这些应用程序不能太新（毕竟安卓4.3），不能太大（当场卡死警告），不能吃性能（当场卡死警告*2）。所以自然的，我把目光投向安卓生态圈，试图从里面寻找堪用的软件。

由于我在 PC 端使用的是由[一座桥在水上](https://blog.othing.xyz/)提供的 FRESSRSS 服务，所以我首先考虑的是支持 FRESSRSS 同步的软件。但无论是 FeedMe 还是 Easy Rss， 都无法登录。我花了几天时间寻找问题，结果发现，若使用黑莓自带的安卓模拟器中的上网组件，便无法访问[一座桥在水上](https://blog.othing.xyz/)的域名。也许是证书问题，也许是其它，总之，本人无力解决这一问题。

怎么办呢？

# TTRSS+FEEDME

好在，提供免费RSS订阅服务的大佬不止一个，在[这里](https://github.com/AboutRSS/ALL-about-RSS#-free-servers)可以找到免费RSS的订阅服务。经过测试，我选择的是[思有云 - IOIOX](https://www.ioiox.com/)提供的 [Tiny Tiny RSS 订阅服务](https://rss.ioiox.com/)，以及安卓端 RSS 阅览器 [FeedMe](https://github.com/seazon/FeedMe) 的3.9.3版本

[思有云上的 RSS 介绍](https://www.ioiox.com/archives/94.html)

[FeedMe的3.9.3版本（提取码：oidm ）](https://pan.baidu.com/s/1Fhe5K5ZlWCtpmqkgi145KQ )



> 在此提供一个测试网址的方法：下载via浏览器的`APK`安装包，并安装在手机上，使用其访问网址以确认其可用性。

