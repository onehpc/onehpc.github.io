---
title: centos安装显卡驱动
date: 2022-09-19 10:13:11
updated: 2022-09-19 10:13:11
comments: true
---
<!--StartFragment-->

屏蔽系统自带的 Nouveau 显卡驱动

# [](https://c3.pw/index.php/archives/5/#cl-1)通过vim编辑器更改配置文件，按照以下内容进行修改

# [](https://c3.pw/index.php/archives/5/#cl-2)vim /lib/modprobe.d/dist-blacklist.conf

最底下加入下面两行\
blacklist nouveau\
options nouveau modeset=0

# [](https://c3.pw/index.php/archives/5/#cl-3)将nvidiafb的这一行注释掉

# [](https://c3.pw/index.php/archives/5/#cl-4)blacklist nvidiafb

保存退出\
重建 initramfs imagen内核\
备份\
mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r).img.bak\
重建\
dracut /boot/initramfs-$(uname -r).img $(uname -r)

# [](https://c3.pw/index.php/archives/5/#cl-5)修改系统运行级别为纯文本模式

# [](https://c3.pw/index.php/archives/5/#cl-6)systemctl set-default multi-user.target

# [](https://c3.pw/index.php/archives/5/#cl-7)重启系统

# [](https://c3.pw/index.php/archives/5/#cl-8)reboot

# [](https://c3.pw/index.php/archives/5/#cl-9)系统重启完成后，在纯文本模式下使用root用户登录进系统

# [](https://c3.pw/index.php/archives/5/#cl-10)查看nouveau显卡驱动是否已经被禁用，若此命令执行完之后没有输出相关信息，则说明已经被禁用

# [](https://c3.pw/index.php/archives/5/#cl-11)lsmod | grep nouveau

变为可执行文件\
chmod +x 英伟达驱动\
安装驱动\
./英伟达驱动

# [](https://c3.pw/index.php/archives/5/#cl-12)安装过程中，选择accept；如果提示要修改xorg.conf，选择yes；

# [](https://c3.pw/index.php/archives/5/#cl-13)查看显卡驱动的安装状态，若此命令执行完之后正常输出显卡状态相关的信息，则说明Nvidia显卡驱动安装成功

# [](https://c3.pw/index.php/archives/5/#cl-14)nvidia-smi

# [](https://c3.pw/index.php/archives/5/#cl-15)修改系统运行级别为图形模式

# [](https://c3.pw/index.php/archives/5/#cl-16)systemctl set-default graphical.target

重启

# [](https://c3.pw/index.php/archives/5/#cl-17)reboot

<!--EndFragment-->