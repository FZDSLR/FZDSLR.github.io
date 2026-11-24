---
title: 在黑莓9900上使用XPRSS查看RSS消息（进阶篇）
date: 2020-06-29 22:30:00
cover: https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/xprss2-zhuti1.jpg
tags:
  - Blackberry
  - RSS
categories:
  - Blackberry
---

# 前言

上一篇文章大致介绍了使用XPRSS订阅RSS消息的方法。但是问题在于：

1. 由于XPRSS似乎依赖自带的浏览器工作，所以造成一个结果：自带浏览器（由于那巨坑的证书问题）访问不了的网址，XPRSS也访问不了。所以有些网站提供的RSS订阅源是无法被XPRSS打开的。
2. 还有很多网站不提供RSS订阅服务。

俗话说，车到山前必有路<s>（不管你们信不信反正我是信的）</s>。面对这些问题，我们仍然可以通过一些非同寻常的方法来解决。

# 已有全文RSS？

如果已经有了全文RSS，只是因为浏览器的证书问题而无法打开，那么可以使用一款名为[RSSMix](http://www.rssmix.com/)的工具进行转制。

RSSMix的本职工作，顾名思义，是将多个RSS源的消息混合在一起，形成一个新的RSS源。由于它并不使用`HTTPS`，因而无证书无效之忧。<s>（没有`HTTPS`竟然还能成为一种优点233333）</s>

使用方法很简单：将源**分行**填入第一个框中，在`Mix Title`框中填上新源的名字（不重要，反正在XPRSS里可以改），然后点击`Create!`，就可以创建出一个新源了。

如果只想让这个源包含一个RSS源，怎么办呢？这里给出一种方法：

- 自己写一个`xml`或者`rss`文件，注意里面的日期最好够老

- 把文件扔到Github里

- 在RSSMix的界面填写你想显示的源的地址+GitHub中文件的地址

  > 可以使用Jsdelivr的加速服务
  >
  > 文件位置：https://cdn.jsdelivr.net/gh/`用户名` /`仓库名`/`文件名`

当然如果懒得折腾，你可以使用[我的`xml`地址](https://cdn.jsdelivr.net/gh/FZDSLR/WDCK-1/ky1.xml)。

PS：RSSMix在你访问新源时才会读取旧源，故大多数情况下你读到的RSS源的时间截止到你上次访问新源的时间。所以如果想阅读新的消息，可以访问一下新源，隔一段时间（一两分钟差不多），再访问一次。

PSS：当然也可以用它来转发Feed43的源。

![比如这样...](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/xprss2-zhuti1.jpg)

# 只有摘要？

某些RSS源只有摘要信息，此举意在吸引读者进入源网站访问，或者是利用如[Feed43](https://feed43.com/)之类工具转制的RSS源。

如果想阅读这些源中的全文消息，那么需要使用RSS全文扩展工具。个人使用的是[FiveFilters](http://ftr.fivefilters.org/)。

使用方法非常简单：在`Enter URL`中填写摘要RSS的地址，然后点击``Create Feed`即可。

![RSSHub——观察者网输出演示](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed//Tec/xprss2-gcz1.jpg)

不过该方案似乎无法获得Feed43的全文，这是很遗憾的一点。

# 寻找、处理RSS源

Github上有人整理了一个[非常全面的工具合集](https://github.com/AboutRSS/ALL-about-RSS)。我也把我现在使用的一些工具列出来。

- [Feed43](https://feed43.com/)：为不提供RSS的网站制作摘要RSS源。

- [FiveFilters](http://ftr.fivefilters.org/)：摘要RSS转全文RSS。

- [RSSMix](http://www.rssmix.com/)：RSS混合(和代理)工具

- [RSSHub](https://docs.rsshub.app/)：提供数目庞大的RSS订阅源。（可惜黑莓9900浏览器打不开，需配合RSSMix和FiveFilters工作）

  [Github地址](https://github.com/DIYgod/RSSHub)

- [morerssplz](https://rss.lilydjwg.me/)：订阅知乎专栏、动态、话题消息。（需配合RSSMix和FiveFilters工作）

  [Github地址](https://github.com/lilydjwg/morerssplz)

- [FeedX](https://feedx.net/)：提供国内外媒体的全文RSS，质量上乘，主域名`.net`由于众所周知的原因不能访问，备用域名几个月一换，推荐使用主域名配合RSSMix订阅。

