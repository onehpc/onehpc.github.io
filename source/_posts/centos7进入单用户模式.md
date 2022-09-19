---
title: centos7进入单用户模式
date: 2022-09-19 10:03:13
updated: 2022-09-19 10:03:13
comments: true
---
<!--StartFragment-->

一、开机时进入如下界面，（按下方向键盘，阻止系统自动继续）\
[![5i1Fx.png](https://i.w3tt.com/2021/09/27/5i1Fx.png "5i1Fx.png")](https://i.w3tt.com/2021/09/27/5i1Fx.png)

按e键出现下面界面

[![5i7Pj.png](https://i.w3tt.com/2021/09/27/5i7Pj.png "5i7Pj.png")](https://i.w3tt.com/2021/09/27/5i7Pj.png)

按方向键下，定位到最后，找到“ro”一行，ro的意思是read only，将“ro”替换成 rw init=/sysroot/bin/sh，如下图\
[![5iN9p.png](https://i.w3tt.com/2021/09/27/5iN9p.png "5iN9p.png")](https://i.w3tt.com/2021/09/27/5iN9p.png)

二、按Ctrl-x 进行重启进入单用户模式

三、执行chroot /sysroot。其中chroot命令用来切换系统，/sysroot/目录就是原始系统

:/# chroot /sysroot\
:/#\
四、如果要修改root密码

passwd是修改root密码的命令,touch /.autorelabel 执行这行命令作用是让SELinux生效，\
如果不执行，密码不会生效。按Ctrl+D，执行reboot重启生效。如下图

五、如果因为启用x-window或者显卡驱动更新，无法进入桌面，可以修改默认启动级别（开机进入命令行模式）

systemctl set-default multi-user.target #设置成命令模式\
init 3 # 切换到字符模式，有时只使用上面的语句没有效果\
按下Ctrl+D后，执行reboot

<!--EndFragment-->