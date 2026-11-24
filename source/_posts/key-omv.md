---
title: Key社Gal中OMV文件的转码方法
cover: https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/acg/SP/bg201e.png
date: 2020-05-22 22:00:00
tags:
  - GALGAME
  - 技术
categories:
  - 技术
---

# 前言

自己在网上找`OMV`文件的转码找了很久，在此留个档。

# 什么是`OMV`文件？

![效果演示](https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/ef_butterfly02.gif)

本篇文章中提到的`OMV`文件，是如Key社的Galgame中的带alpha通道的动态图文件。

这类效果对于制作静止系MAD之类的东西**非常有用**<span class="heimu" title="嘿嘿嘿">不然我解包这个干吗</span>

# 实现方法

主要借助`SiglusExtract`下的`Omv2Avi.exe`。

## 下载工具

`SiglusExtract`的Github项目地址为：`https://github.com/xmoeproject/SiglusExtract`

如果速度太慢的话，推荐使用[GitHubd](https://githubd.com/#/)进行下载。

## 开始转码！

1. 打开 `SiglusExtract\tools`，找到`Omv2Avi.exe`

2. 找到Galgame的OMV文件，将其拖拽到`Omv2Avi.exe`上

3. 应该会跳出一个窗口，这表明正在转码

   <img src="https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/OMVTOAVI1.jpg"/>

4. 然后就可以在该`OMV`文件目录下发现同名的`AVI`文件了。

# 注意！

1. 转出来的`AVI`文件体积巨大，如果硬盘空间很小很小很小的谨慎使用.

   <img src="https://cdn.jsdelivr.net/gh/FZDSLR/buran-picture-bed/Tec/OMVTOAVI2.PNG"/>

2. 转出的`AVI`并不完美（可能是软件本身的问题w），可能会有一些格式上的问题（导到Pr里各种报错不过还能用233）。

