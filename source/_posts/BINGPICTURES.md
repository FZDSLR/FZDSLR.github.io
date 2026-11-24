---
title: HEXO-Butterfly主题右侧添加Bing每日图片
cover: https://api.dujin.org/bing/1366.php
date: 2020-04-14 16:30:00
tags:
  - Hexo
categories:
  - Hexo


---



> 本文基于 [HCLonely添加组件的方法](https://blog.hclonely.com/posts/57bd67ce/)以及[缙哥哥的Bing每日图片API](https://www.dujin.org/3618.html)，在此表示感谢。

> 因为懒<span class="heimu" title="那与咸鱼有什么区别">其实是不好意思直接整段搬运</span>所以具体步骤请直接参考HCLonely[添加PIXIV组件的方法](https://blog.hclonely.com/posts/57bd67ce/#pixiv日榜)

# 顺带一提
  - 本页面的封面图即为[Bing每日图片](https://www.dujin.org/3618.html)。
  - 可能存在缩进上的问题，如果报错请详细检查错误代码。

# `card_bingpicture.pug`内容

```
.card-widget.card-bingpicture
 .card-content
  .item-headline
    i.fa.fa-image(aria-hidden="true")
    span= _p('aside.card_bingpicture')
  img(src='https://api.dujin.org/bing/1366.php', width='99%')
```
# `index.pug`添加
```
      if theme.aside.card_bingpicture
        include ./card_bingpicture.pug
```
# `butterfly.yml`添加
`card_bingpicture: true`


# `ZH-CN.yml`添加
`card_bingpicture: Bing每日图片`
