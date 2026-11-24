---
title: wayland+平铺+华丽特效——Hyprland 混成器简单使用体验
categories:
 - 技术
tags: 
 - 技术
 - Linux
 - Hyprland
cover: https://cdn1.fzdslr.cn/Pic/Tec/1682331676_grim.png
date: 2023-06-02 22:00:00
---

## 前言

不得不说 wlroots 是一个好东西，许多 Wayland 下的窗口混成器都基于它。我之前介绍过同样基于 wlroots 的 Sway 平铺式窗口管理器。Sway 的使用体验还是非常不错的，日常使用也比较稳定，但是一大痛点就是不大美观——不支持窗口模糊和各种动画，以至于除了滑动浏览器页面的时候画面不会撕裂之外完全没有用 Wayland 的实感（哦不还有折腾 Xwayland 的时候）。正好（？）之前那台 chromebook pixel 2013 的屏幕坏了，搜了搜换屏幕还不如再捡一台洋垃圾 chromebook，于是现在日用的 chromebook 变成了华硕的 C302A——一个非常标准的 12 寸二合一本，支持触摸操作与折叠，并且重量只有1.1千克，配上一个 PD 充电器就可以塞进单肩包到处跑了。在这台机器上试着使用了一段时间的 Hyprland 窗口管理器，体验还算不错。

![配置效果](https://cdn1.fzdslr.cn/Pic/Tec/1682578651_grim.png)

## 简单配置

配置文件位于 `~/.config/hypr/hyprland.conf`。跟 Sway 的配置文件不同的地方在于修改并保存完配置文件后不需要手动刷新，Hyprland 会自动更新。

和 Sway 一样，配置 Hyprland 的第一步是设置快捷键。由于使用的是 chromebook 的键盘，我选择将 Alt 键设置为主要 Mod 键：

```
$mainMod = ALT
```

然后就可以在后面的配置文件中用 `$mainMod` 指代 ALT 键了。详细的键位绑定参考[官方文档](https://wiki.hyprland.org/Configuring/Binds/)。

音量和亮度快捷键写法跟 Sway 基本一致：

```
bind=, XF86AudioMute, exec, pactl set-sink-mute @DEFAULT_SINK@ toggle
binde=, XF86AudioLowerVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ -2%
binde=, XF86AudioRaiseVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ +2%
bind=, XF86AudioMicMute, exec, pactl set-source-mute @DEFAULT_SOURCE@ toggle

binde=, XF86MonBrightnessDown, exec, brightnessctl --device=intel_backlight set 3%-
binde=, XF86MonBrightnessUp, exec, brightnessctl --device=intel_backlight set +3%
```

对于 chromebook 来说，`input` 需要配置 ` kb_model = chromebook`

Hyprland 有两种窗口平铺模式，分为 Dwindle Layout（类似 bspwm）与 Master Layout（类似 i3），可以根据自己的需要进行选择。

Hyprland 原生支持用触摸板手势切工作区（配置 `gestures` 中的 `workspace_swipe_xxx` 选项即可）。至于工作区切换方向（上下或左右），需要在 `animations` 中的 `animation = workspaces,......` 的最后一项中配置，我选择的是上下滑动，所以最后的选项是 `slidevert
`。

### 状态栏

如果图省事的话，使用 waybar 是最省时间的，但是不能直接使用官方版本（工作区无法正常显示），需要在 AUR 安装 `waybar-hyprland`。不过我电脑上始终有一个 Sway 备用，而如果安装这个分支，waybar 在 sway 上便无法正常显示工作区了。所以我安装了 [eww](https://github.com/elkowar/eww)，也能用，只是写脚本麻烦点而已。

### 应用启动器

继续使用 Wofi 即可。顺带一提，如果要模糊 Wofi 的半透明背景，那么 Hyprland 的配置文件需要加一行 `blurls=wofi`。但是这种做法的代价是，在 Wofi 的框里用输入法打字的时候有 bug，输入法的框疑似会被认为是一个平铺窗口。不过正常情况下打几个英文字母就可以选到正确的内容，也不需要调用输入法输入中文。

### 通知

使用 mako。

### 主题

配置 GTK 主题用的是 `lx-appearance`，配置 QT 主题用的则是 `Kvantum`。目前桌面的配色主要参考 [Rose-pine](https://rosepinetheme.com/)。

### 壁纸

我使用的是 [swww](https://github.com/Horus645/swww)，每次启动桌面的时候需要执行一个小脚本：

```
#!/bin/bash

swww init
swww img 图片路径
```

swww 有很多可选的特效，但是我对实时换壁纸这种事没什么需求所以就没有研究。

## 小结

Hyprland 用起来给我的感觉是一个“画面更精致的 sway”，它的（相对流畅的）窗口特效把 Wayland 相对于 X11 的优势发挥了出来。虽然有时候还会碰到一些小问题，但总的来说还是很值得尝试的。

PS：关于这台新 chromebook 我或许也会写一篇文章讲一讲折腾的过程——只要有时间的话......
