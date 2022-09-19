---
title: centos7安装xrdp远程桌面服务
date: 2022-09-19 10:04:48
updated: 2022-09-19 10:04:48
comments: true
---
<!--StartFragment-->

更新epel\
`yum -y install epel-release`\
安装Xrdp\
`yum -y install xrdp`\
安装完成之后，设置开机启动并启动xrdp\
`systemctl start xrdp && systemctl enable xrdp`

连接时闪退\
将anaconda环境变量的顺序往后移动

# [](https://c3.pw/index.php/archives/19/#cl-1)修改前

`export PATH=/opt/anaconda3/bin:$PATH`

# [](https://c3.pw/index.php/archives/19/#cl-2)修改后

`export PATH=$PATH:/opt/anaconda3/bin`

# [](https://c3.pw/index.php/archives/19/#cl-3)修改前

`export PATH=/usr/local/cuda/bin/:$PATH`

# [](https://c3.pw/index.php/archives/19/#cl-4)修改后

`export PATH=$PATH:/usr/local/cuda/bin/`\
和vnc不一样，这个多人使用的话，给每个人建立一个用户。

<!--EndFragment-->