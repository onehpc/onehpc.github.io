---
title: win10和ubuntu双系统设置默认启动系统为win10
date: 2022-11-17 16:38:20
updated: 2022-11-17 16:38:20
comments: true
---
<!--StartFragment-->

在win10下安装了Ubuntu20.04系统，默认情况下，启动的是[Ubuntu](https://so.csdn.net/so/search?q=Ubuntu&spm=1001.2101.3001.7020)系统。

要将默认启动系统设置成win10，方法如下：

1、进入ubuntu系统，按住Ctrl+Alt+T键，打开终端。

2、输入命令：

或进入/etc/default/文件夹下，打开终端，输入命令：

sudo gedit grub

将第6行GRUB_DEFAULT=0修改为想要默认启动的系统序号，设置完后保存；

系统序号即为启动时的菜单顺序，从0开始数，Ubuntu默认为第一个，序号为0，win10系统一般在第5个，序号为4，所以设置GRUB_DEFAULT=4。



3、输入 (sudo) update-grub 命令更新grub文件

4、重启系统即可默认进入Windows系统。

<!--EndFragment-->