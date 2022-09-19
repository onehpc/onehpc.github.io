---
title: ubuntu安装英伟达显卡
date: 2022-09-19 10:09:13
updated: 2022-09-19 10:09:13
comments: true
---
<!--StartFragment-->

第一步 先禁用ubuntu 自带显卡驱动\
如果未安装vim\
sudo apt install vim\
sudo vim /etc/modprobe.d/blacklist.conf\
最后一行加上:\
blacklist nouveau\
options nouveau modeset=0\
保存退出\
sudo update-initramfs -u 使禁用 nouveau 真正生效\
必须重启reboot\
安装显卡驱动要先切换到文字界面，(按Ctrl+Alt+F3)\
使用命令，查看nouveau是否被禁用，无任何输出禁用nouveau成功\
lsmod | grep nouveau\
禁用ubuntu 图形界面\
sudo service lightdm stop\
然后cd 英伟达驱动目录中\
chmod +x 英伟达驱动\
sudo ./英伟达驱动\
按照提示一步步来完成后 ，在输入 init 5 进入图形界面\
验证驱动安装成功 sudo nvidia-smi\
有显卡型号，安装成功。

<!--EndFragment-->