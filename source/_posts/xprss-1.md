---
title: 在黑莓9900上使用XPRSS查看RSS消息
cover: https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/acg/MSN/MSNWHJ1-05.png
date: 2020-06-13 20:00:00
tags:
  - Blackberry
  - RSS
categories:
  - Blackberry
---

# 前言

对黑莓9900这台名不副实的“智能机”进行各种折腾，实乃无奈之举（苦逼高中生.jpg）。在一年的使用过后，也积累了一些非常实用（折腾无比）的技巧和工具。

鉴于黑莓的可怜巴巴的浏览器，可怜巴巴的内存，可怜巴巴的证书，可怜巴巴的生态环境，可怜巴巴的屏幕，等等。总之，在9900上打开新闻网站是一件十分令人恼火的事情，因为您可能遭遇如下情况：

1. 通讯故障。服务器可能正忙，请稍后重试。如果问题仍然存在，请与服务提供商联系。
2. 无法使用当前的安全性设置进行连接。请与服务提供商联系。
3. 在打开网页时，由于网页相对于您的浏览器过于复杂，导致闪退或卡死。
4. 花了n（n>3）分钟打开网页

千辛万苦，终于打开网页后

- 超链接无响应
- 字体极小
- 网页不会自适应屏幕，以至于不得不不断左右移动光标

等等。

即使顺利地看完了新闻，这个过程所花掉的时间也是相当可观的。

怎么办呢？

这时就要请出这个重量级工具——RSS阅读器。

# 什么是RSS

引用一下维基百科的解释：

> RSS（简易信息聚合）是一种消息来源格式规范，用以聚合经常发布更新数据的网站，例如博客文章、新闻、音频或视频的网摘。

举个例子。我们打开 [人民网财经频道的RSS源](http://www.people.com.cn/rss/finance.xml)

```
<item>
<title>
<![CDATA[ 商务部：帮助外贸企业渡难关、保市场、保订单 ]]>
</title>
<link>http://finance.people.com.cn/n1/2020/0612/c1004-31745306.html</link>
<pubDate>2020-06-12</pubDate>
<author>人民网</author>
<description>
<![CDATA[ <p style="text-indent: 2em;"> 人民网北京6月12日电 （孙阳）1-5月，受疫情影响，我国进出口总额11.54万亿元人民币，下降4.9%。其中，出口6.2万亿元，下降4.7%；进口5.34万亿元，下降5.2%。5月当月，我国进出口总额2.47万亿元，下降4.9%。其中，出口1.46万亿元，增长1.4%；进口1.01万亿元，下降12.7%。商务部外贸司负责人表示，1-5月，外贸运行主要呈现以下特点：</p> <p style="text-indent: 2em;"> 一是对新兴市场出口好于整体。对新兴市场出口下降2.9%，降幅好于整体1.9个百分点，占比提升0.9个百分点至49.7%。其中，对东盟出口增长2.8%，增幅好于整体7.5个百分点，占比提升1个百分点至15.1%。对传统市场出口下降6.5%，占比下降至50.3%。</p> <p style="text-indent: 2em;"> 二是民营企业出口占比提升。民营企业出口微降0.3%，降幅好于整体4.4个百分点，展现较强韧性和活力，占比提升2.4个百分点至52.9%。国有企业、外资企业出口分别下降8.4%、9.4%。</p> <p style="text-indent: 2em;"> 三是机电产品出口好于整体。机电产品出口下降4.0%，降幅小于整体0.7个百分点，占比达61.1%。其中，集成电路、电脑出口增长14.5%、1.8%。劳动密集型产品受境外疫情影响较大，服装、箱包、鞋、玩具、家具等产品出口合计下降20.3%。防疫物资成为出口增长的亮点。口罩带动纺织品增长25.5%，医疗器械、中药材增长33%、8%。</p> <p style="text-indent: 2em;"> 四是中西部地区出口占比提升。中西部地区出口下降0.2%，降幅好于整体4.5个百分点，占比提升0.8个百分点至18.4%。东部地区出口下降5.7%，降幅深于整体1个百分点，占比下降至81.6%。</p> <p style="text-indent: 2em;"> 五是主要大宗商品进口量增价跌。受国际市场需求疲软影响，大宗商品价格普遍下跌。原油、天然气、铜、煤炭、大豆等进口价格分别下降21.2%、14.7%、6.3%、4.7%、1.7%，进口量分别增长5.2%、1.9%、12.4%、16.8%、6.8%。仅这些商品价格下跌就拉低进口增速3个百分点。</p> <p style="text-indent: 2em;"> 今年以来，为应对疫情对我国外贸发展造成的冲击，国务院及时出台一系列稳外贸政策措施，主要包括完善出口退税政策、增加外贸信贷投放、加大出口信用保险支持、增设跨境综试区、支持出口转内销等方面，商务部会同各地方、各部门狠抓政策落实，帮助企业纾困解难，抢市场抓订单，努力将疫情对外贸影响降到最低。</p> <p style="text-indent: 2em;"> 当前，全球疫情仍在恶化，新增病例数屡创新高，世界经济严重衰退，国际需求急剧萎缩。虽然一些国家和地区“带疫解封”，但需求恢复仍需时日，我国外贸发展面临的不确定性、不稳定性因素显著增多，风险和挑战前所未有，下行压力进一步加大。</p> <p style="text-indent: 2em;"> 商务部外贸司负责人介绍说，下一步，商务部将按照党中央、国务院决策部署，扎实做好“六稳”工作，全面落实“六保”任务，帮助外贸企业渡难关、保市场、保订单，保障产业链供应链稳定，在网上办好第127届广交会，支持加工贸易出口转内销，加快跨境电商等贸易新业态发展，积极扩大进口，推进贸易高质量发展，全力以赴完成进出口促稳提质目标任务，为决胜全面建成小康社会、打赢脱贫攻坚战作出积极贡献。</p> ]]>
</description>
</item>
```



> 本条RSS节选于2020.06.12

夹在`<item>`和`</item>`之间的就是一条新闻。它包括：

- `<title>`：标题
- `<link>`：新闻链接
- `<pubDate>`：发布时间
- `<author>`：编者
- `<descripton>`：内容

可以看到，这些要素恰好可以构成一篇新闻。

RSS阅读器，可以通过读取这些信息，进行渲染，从而将整理后的信息呈现出来。

# 安装XPRSS

首先，我们需要有一个RSS阅读器。这里介绍黑莓应用商店中的一款RSS阅读器——XPRSS。

直接在`BlackBerry App World`的搜索框中输入`XPRSS`，看到后按流程安装即可。

![](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS0.jpg)

# 开始使用！

## 网络设置

这个RSS阅读器，老实说，体验并不是特别好，至少Bug这种东西有着不少，不过黑莓9900嘛......能用就行。

首先，在打开APP之前，请务必在`选项/网络和连接/移动网络`中把`数据服务`设置为`开`，不然之后阅读器会提示`Network Unavailable`。

![开启数据服务](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS01.jpg)

如果你像我一样，是个套餐里连1b流量都没有的学生党<s>（然而其实有10Mb）</s>，那么为了防止意外的流量消耗，那么打开APP，按一下黑莓键，在弹出的左侧菜单中选择`Options/Network Settings`，然后只勾上`Wifi`。

![只勾选Wifi](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS2.jpg)

## 分类

在XPRSS中，RSS源被归类在分类下。

不出意料的话，在刚刚安装完软件后，XPRSS会自动创建好一些分类。

如果想对分类进行操作，那么请按下黑莓键以调出菜单，抑或长按分类以调出简略版菜单。

- Add Category：增加分类

- Delete Category：删除分类

- Edit Category：编辑分类

  > Edit Category中有两栏。`Category Title`中填标题名称，`Category Thumbnail`中选择图标。
  >
  > ![](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS3.jpg)

- Move up：向上移动

- Move down：向下移动

**务必注意！**删除分类时**不会再次询问！不会再次询问！不会再次询问！**

这意味着如果手滑点到`Delete Category`，那么光标所停留的分类将被**直接删除**，没有挽回的余地。

但后果严重吗？老实说，如果你时间充裕，后果也没多严重，不过是再创建一个分类，再**一个一个**解析RSS源地址、添加到分类而已。不过，<br>**时间就是金钱啊，同志！**

所以我强烈推荐创建一个空分类，在执行一些操作（主要是退出程序），需要调出菜单时，把光标移到那个分类上面，再进行操作。这样即使不小心点到了`Delete Category`，所损失的也不过是花掉15s就能重建的空分类而已。

## 添加源

按下黑莓键，调出菜单，选择`Add Feed`，开始添加源。

不出意料的话，弹出的界面中会有四个部分。日常使用中主要使用第一个`Enter a feed URL.`选框。

![](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS4.jpg)

使用方法很简单：把RSS源“如`http://www.people.com.cn/rss/finance.xml`”填写至选框中，然后点击`Validate`，出现新界面后，编辑标题和分类，然后点击`Save`，该RSS源就添加至分类目录下了。

![](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS5.jpg)

## 阅读源

打开分类，找到你所添加的源，直接打开，即可看到新闻列表。

![](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS7.jpg)

点击新闻以观看。

![](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/XPRSS8.jpg)

## 一些可用的官方源

### 人民网

国内新闻：`http://www.people.com.cn/rss/politics.xml`

国际新闻：`http://www.people.com.cn/rss/world.xml`

经济新闻：`http://www.people.com.cn/rss/finance.xml`

体育新闻：`http://www.people.com.cn/rss/sports.xml`

若需要更多的源，请前往 [人民网的RSS页面](http://rss.people.com.cn/)。

### 环球网

`http://rss.huanqiu.com/topnews.xml`

### 知乎每日精选

`https://www.zhihu.com/rss`

### 俄罗斯卫星通讯社

`http://sputniknews.cn/export/rss2/archive/index.xml`

### ACG批评

`http://www.acgpiping.net/feed/`

更多的源可以在网上慢慢寻找。

# 还有一件事

然而，还有很多网站是不提供RSS订阅服务的。但那并不意味着我们对此无计可施。方法将在下一篇文章中记录。