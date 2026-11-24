---
title: 在黑莓9900上使用XPRSS查看RSS消息（扫尾篇）
cover: https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS3-3.jpg
date: 2020-07-12 00:00:00
tags:
  - Blackberry
  - RSS
categories:
  - Blackberry
---

# 几个痛点

XPRSS的问题主要体现在以下几点：

1. 黑底白字，且无法更改字体大小。

   阅读中文这种单字信息量比较大的文字还好，RSS源的语言是英文的时候，那显示效果就......

   天知道开发者是怎么忍得了这种显示方式的。<span class="heimu" title="你知道的太多了">可能这就是开发者的癖好吧</span>

2. 超链接经常被诡异地拉长，且很多时候无法点击。

   <img src="https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS3-2.jpg" style="zoom:50%;" />

3. 使用和自带浏览器相同的安全性设置。

4. 必须要点进单个源后才能得知源的更新情况。

5. 无法加载一些`css`和`js`，导致文章无法显示（比如本博客的RSS源）

   <img src="https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS3-1.jpg" style="zoom:50%;" />

不过，这些问题都是小事情，毕竟黑莓9900，啊，能用就行<span class="heimu" title="你知道的太多了">(确信</span>

# 一些小功能

## 在网站上寻找RSS源，以及批量添加RSS源

在添加RSS源时，我们通常只使用`Add Feed`中的`Enter a feed URL.`选框。在这里顺便讲一讲下面的三个框是干什么用的。

<img src="https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS4.jpg" style="zoom:50%;" />

如果在`Enter a web address.`里填上一个网站地址，再点击`Search for feeds`，那么XPRSS会在该页面自动寻找RSS源的地址，并解析到XPRSS中。

在`Enter an OPML URL.`填上一个（有着几个RSS源地址的）`OPML`文件的地址，可用于批量导入RSS订阅源。

>  这里提供`OPML`文件测试，该文件由[Ricky](https://www.zhihu.com/question/19580096/answer/119486747)提供，不过由于众所周知的原因，现在`https://raw.githubusercontent.com/`无法访问，所以我把它转移了一下。现地址为`https://cdn.jsdelivr.net/gh/FZDSLR/WDCK-1/OPML.xml`。

最后的`Enter a topic`似乎可以将搜索引擎的搜索结果转换为RSS条目的形式，不过Google和Yahoo在国内都连不上，Bing虽然可以生成源，但源里面不会有任何条目出现。**总而言之，这个功能完全没法用。**

## 缓存

在`Options`-`Local Cache`中可以开启文章缓存，这样即使是在没网的时候，你也可以阅读之前的文章。

<img src="https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS3-3.jpg" style="zoom:50%;" />

需要注意的是

- 不能针对单一源修改缓存数目。
- 文章中的外链图片将不会被缓存。