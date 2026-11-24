---
title: 在 Chromebook Pixel 2013 上安装 ArchLinux + Sway
categories:
 - 技术
tags: 
 - 技术
 - Linux
 - Sway
cover: https://cdn1.fzdslr.cn/Pic/Tec/1647790847_grim.jpg
date: 2022-03-25 22:30:00
description: Chromebook Pixel 2013 是谷歌于 2013 年发售的一款 Chromebook。
---

## 前言

Chromebook Pixel 2013 是谷歌于 2013 年<s>这不是废话吗</s>发售的一款 Chromebook。它拥有：
- 三代低压I5（Intel i5-3427U）
- 一块 2560x1700 的 12 寸 2K 触摸屏
- 4GB 内存
- 64GB emmc

以今天的标准来看，其 CPU 性能可以说是远远不够看，4+64 的配置也是吊车尾水平，但是这块屏幕却非常亮眼——2K 的分辨率外加 12 寸的小尺寸，这使得其 dpi 达到了惊人的 239，视觉效果理论上非常不错。

作为 Chromebook，其预装的自然是 ChromeOS 系统。不过由于这台机器年代实在过于久远，谷歌早已停止对它的支持，这台机器处于所谓"EoL"(End of Life)状态下。其原版的 ChromeOS 由于网络与生态问题，在国内使用体验并不好。好在查阅相关资料后，我发现这台机器可以通过刷 BIOS 的方式安装原生的 Linux。于是我就在海鲜市场以600出头的价格搞了一台 Chromebook Pixel 2013，到货后旋即开始折腾。

## 刷 BIOS

首先解释一下为什么要刷 BIOS。

年代相当久远的一个在 Chromebook 中安装其他系统的方法是启用 Legacy Bios。在 ChromeOS 的终端中运行

```
crossystem dev_boot_usb=1 dev_boot_legacy=1
```

这样一来，再次开机时，即可按 Ctrl+L 进入 SeaBIOS，继而进入插在 USB 口上的安装盘或者安装在机器上的其他系统。但是这个方法存在一个问题：这两个标志是存在 RAM 里的，在机器电池几乎耗尽（我看到的一个案例是剩下约15%）后，便会回到原先状态。如果机器上保存了原先的 ChromeOS 系统还好一点，再操作一遍就行了，如果没有嘛……

这就是为什么 [InstallOnDebian](https://wiki.debian.org/InstallingDebianOn/ChromebookPixel) 上会郑重地标注：

> It's very important not to let the battery run completely out or you may lose all your data!

在现在，个人认为刷写 MrChromebox 的第三方固件是最好的选择。刷写过程可以参考 [FydeOS 针对此机型编写的刷写文档](https://faq.fydeos.com/recipes/chromebook-pixel-2013-firmware/)，除了“进入通过 USB 存储设备启动的 FydeOS 中执行 Installer 程序完成 FydeOS 的安装。”不用做<s>想试试也行</s>之外，其他步骤都是一样的。也可以同时参考[他们的视频](https://www.bilibili.com/video/BV1uV411S7SW)。

> 虽然说看起来步骤非常简单，但实际操作就是另一回事了。我折腾一晚上，愣是拧不开这台机器的保护螺丝，拿到熟人的电脑店里五秒钟拧开，合适的工具确实非常重要。
> 
> ![那颗写保护螺丝](https://cdn1.fzdslr.cn/Pic/Tec/IMG_20220207_204048-1.jpg)
## 装 Linux

我曾经考虑过要不要装 Debian testing，但是想了想还是决定装 Arch —— AUR，Pacman 和 ArchWiki 实在太香了。

安装 Arch 照着 Wiki 搞就行，没啥技术含量。

因为这台机器的硬盘和内存确实比较小，我没有单独为 `\home` 进行分区，同时另外分配了 4G 的交换空间。

### 桌面环境

桌面环境方面，论对触摸的支持，采用 Wayland 的 DE/WM 肯定要比 X11 好—— X11 会把触摸默认当作鼠标，对于滑动操作很不友好。但是在其他方面，Wayland 还是有很大问题的。

最大的问题是在这块 2K 高分屏上 Xwayland 程序会变得非常模糊——这似乎是 Xwayland 的一个 bug。这使得在 Wayland 环境下，Xwayland 桌面程序近乎不可用。至于原生的 Wayland 程序也有一些问题，比如 Chromium 以及其衍生品，目前在原生 Wayland 模式下，输入法无法正常工作。

**但是**，好在在 AUR 上有 [sway-hidpi-git](https://aur.archlinux.org/packages/sway-hidpi-git) 和 [wlroots-hidpi-git](https://aur.archlinux.org/packages/wlroots-hidpi-git) 两个包，解决了 Sway 中 Xwayland 程序在高分屏上模糊的问题。 

> ArchlinuxCN 源也有这两个包，但是其版本和 AUR 上的可能有一些不同，在安装以及滚动更新的时候可能会出现一些问题。

我安装了 Sway(wayland) 与 KDE(x11/wayland)，配置方面 KDE 要更简单一点，Chromebook 的特殊键盘在 KDE 上设置非常简单，对键盘灯与屏幕亮度的调节也可以说是开箱即用，至于 Sway 就要麻烦很多了——比如默认将 Mod 键配置为左边的 super 键，使得初次进入桌面几乎啥都干不了，只能回到 tty 调整 config 文件。不过 Sway 配置完毕后还是很称手的。

下面写的主要是 Sway 的配置。

![大致效果](https://cdn1.fzdslr.cn/Pic/Tec/1647790847_grim.jpg)

#### 键盘

对于 Sway，在 config 中添加：

```
input "1:1:AT_Translated_Set_2_keyboard" {
xkb_model chromebook
}
```

想要启用屏幕亮度调节按钮，在 config 中添加

```
bindsym XF86MonBrightnessDown exec brightnessctl --device=intel_backlight set 5%-
bindsym XF86MonBrightnessUp exec brightnessctl --device=intel_backlight set +5%
```

> 通过 `brightnessctl` 同样可以调节键盘亮度（`--device=chromeos::kbd_backlight`）

想要启用音量调节按钮，在 config 中添加

```
bindsym --locked XF86AudioMute exec pactl set-sink-mute @DEFAULT_SINK@ toggle
bindsym --locked XF86AudioLowerVolume exec pactl set-sink-volume @DEFAULT_SINK@ -5%
bindsym --locked XF86AudioRaiseVolume exec pactl set-sink-volume @DEFAULT_SINK@ +5%
bindsym --locked XF86AudioMicMute exec pactl set-source-mute @DEFAULT_SOURCE@ toggle
```

#### 输入法

输入法选择 fcitx5，并手动设置自启。

#### 触摸屏

触摸屏有时会突然失灵，特别是从休眠状态唤醒后，此时需要运行

```
sudo modprobe -r chromeos_laptop
sudo modprobe chromeos_laptop
```

当然，比起每次唤醒电脑都手动运行一遍上述命令，让系统在结束休眠的时候自动运行是更好的选择。

```
sudo vim /etc/systemd/system/root-resume.service
```

```
[Unit]
Description=Local system resume actions
After=suspend.target

[Service]
Type=simple
ExecStartPre=modprobe -r chromeos_laptop
ExecStart=modprobe chromeos_laptop

[Install]
WantedBy=suspend.target
```

但是有的时候唤醒后触摸屏还是失灵，这个时候还是需要手动运行一遍命令。

详见 [ArchWiki 上的相关页面](https://wiki.archlinux.org/title/Power_management_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)。

> 注意：由于疑似内核驱动的问题，新的内核在这台机器上无法正常使用休眠，据称切换到4.12版本内核可以解决问题，不过我对休眠暂时没有需求，就没有进行验证。

#### 声音

如果出现耳机孔无法使用，插入耳机后音频仍然从扬声器输出的情况，打开 `alsamixer`，按 s ，选择 `HDA Intel PCH`，移动光标，按 m 依次打开右边**两个** `HP/Speaker` ，退出即可。

蓝牙耳机的表现则比较差——仅仅是可用而已，播放音乐时大概率出现卡顿情况。

#### HiDPI

在 `~/.Xresources` 中添加 `Xft.dpi: 192`，然后 `xrdb -merge ~/.Xresources` 与 `xrandr --dpi 192`

同时在配置文件中加入

```
exec xrdb -load ~/.Xresources
xwayland scale 2
```

#### 终端

如果没有中文输入需求可以使用 alacritty ，我是直接使用 KDE 的 Konsole。

#### 程序启动器

使用 [Wofi](https://hg.sr.ht/~scoopta/wofi) 。

#### 状态栏

原版状态栏比较简陋，我使用的是 [Waybar](https://github.com/Alexays/Waybar)，需要在 Sway 的 config 中把 `bar{  }` 中的其他东西注释掉，然后在其中添加 `swaybar_command waybar` 。

#### 触摸板

我设置的是触碰点击，双指右键，三指中键。

```
input "0:0:Atmel_maXTouch_Touchpad" {
dwt enabled
tap enabled
middle_emulation enabled
}
```

触摸板手势使用 [fusuma](https://github.com/iberianpig/fusuma)，配合 [fusuma-plugin-sendkey](https://github.com/iberianpig/fusuma-plugin-sendkey)。使用触摸板手势可以实现一些比较方便的操作，比如三指切换活动窗口，或者四指下扫启动 Wofi。

#### 音乐

个人选择 MPD+ncmpcpp，不过如果喜欢图形化界面的话可以选择 Quod Libet 之类的播放器。

> PS：在`~/Music` 添加关联 SD 卡音乐目录的软链接后 MPD 扫不全我 SD 卡里的歌曲，不知道为什么。

#### 截图

选择 [grim](https://github.com/emersion/grim) 。

```
bindsym $mod2+s exec grim ~/Pictures/Screenshots/$(date +'%s_grim.png') 
bindsym $mod2+Shift+s exec grim -g "$(slurp)" ~/Pictures/Screenshots/$(date +'%s_grim.png')
```

#### 文件浏览器

我选择了命令行界面的 ranger。

#### 文本编辑

Chromium 内核的 VS Code 理论上可以通过传递选项 `--enable-features=UseOzonePlatform --ozone-platform=wayland` 以原生 Wayland 模式运行，但是在 Sway 上传递该选项无法正常唤起 VS code（在 KDE Plasma 上却可以），但是却可以以同样的方式正常唤起原生 Wayland 模式下的 Chromium。好在打了 HiDPI 补丁的 Sway 可以正常运行 Xwayland 下的 VS code 并正常使用输入法。

我目前使用 VS code 的主要原因是跟 LaTeX 有关的 snippets 太多了，迁移到 Vim 上比较麻烦。轻度的文本编辑我还是喜欢使用 Vim，只有在需要写大量数学公式和预览的时候会切到 VS code。

#### 文档阅览

阅读简单的 PDF 文档使用 Zathura 即可。至于复杂的文本编辑，无论是原生支持 Wayland 的 LibreOffice 还是在 Xwayland 下运行的 WPS 都可以使用。

![疫情现状](https://cdn1.fzdslr.cn/Pic/Tec/1647181489_grim.jpg)

#### 关于耗电问题

通过 `acpi -V` 可以方便地查询电源情况。

```
Battery 0: design capacity 8500 mAh, last full capacity 8043 mAh = 94%
```

这一行显示这台电脑的电池健康度。

虽然有 tlp、powertop 之类的电源管理工具，但我并没有采用——之前排查休眠问题的时候全给关了，结果证明跟它们没啥关系。目前我仅使用 `cpupower` 调节 CPU 工作模式。

在满电+低屏幕亮度+不连接 Wifi 的情况下，显示续航时间为七个小时出头。低强度使用下，续航大概有 5-6 个小时。

#### 配置文件

我将配置文件同步到 [Gitee](https://gitee.com/FZDSLR/dotfile) 上了，可供参考。

## 使用体验

在使用过这个本子一段时间之后，总结一下使用体验吧。这是一台优点和缺点都很明显的设备。优点主要是很好的显示效果、较小的尺寸和（目前）相当低廉的价格；而缺点则是比较差的扩展性、很差的性能（特指那块发热量巨大的三代低压I5），以及需要花费大量时间和精力进行折腾。

