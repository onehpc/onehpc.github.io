---
index_img: https://assets.ubuntu.com/v1/741b30ec-desktop-logos.png
title: ubuntu换源
date: 2022-09-19 10:08:32
updated: 2022-09-19 10:08:32
comments: true
---
<!--StartFragment-->

一键脚本\
sudo curl -L <https://github.com/AndyYoungDev/ubuntu-aliyun-sources/releases/download/shell/change.sh> | bash\
1.备份\
/etc/apt/sources.list文件\
mv /etc/apt/sources.list /etc/apt/sourses.list.backup\
2.新建\
新建/etc/apt/sources.list文件并添加以下内容\
在root管理员下\
//切换到管理员\
sudo -i\
//新建文件并写入\
vi /etc/apt/sources.list\
2.1 阿里源：\
deb <http://mirrors.aliyun.com/ubuntu/> bionic main restricted universe multiverse\
deb <http://mirrors.aliyun.com/ubuntu/> bionic-security main restricted universe multiverse\
deb <http://mirrors.aliyun.com/ubuntu/> bionic-updates main restricted universe multiverse\
deb <http://mirrors.aliyun.com/ubuntu/> bionic-proposed main restricted universe multiverse\
deb <http://mirrors.aliyun.com/ubuntu/> bionic-backports main restricted universe multiverse\
deb-src <http://mirrors.aliyun.com/ubuntu/> bionic main restricted universe multiverse\
deb-src <http://mirrors.aliyun.com/ubuntu/> bionic-security main restricted universe multiverse\
deb-src <http://mirrors.aliyun.com/ubuntu/> bionic-updates main restricted universe multiverse\
deb-src <http://mirrors.aliyun.com/ubuntu/> bionic-proposed main restricted universe multiverse\
deb-src <http://mirrors.aliyun.com/ubuntu/> bionic-backports main restricted universe multiverse\
2.2 其它源

# [](https://c3.pw/index.php/archives/13/#cl-1)清华源

deb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic main restricted universe multiverse\
deb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-updates main restricted universe multiverse\
deb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-backports main restricted universe multiverse\
deb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-security main restricted universe multiverse\
deb <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-proposed main restricted universe multiverse\
deb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic main restricted universe multiverse\
deb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-updates main restricted universe multiverse\
deb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-backports main restricted universe multiverse\
deb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-security main restricted universe multiverse\
deb-src <https://mirrors.tuna.tsinghua.edu.cn/ubuntu/> bionic-proposed main restricted universe multiverse

# [](https://c3.pw/index.php/archives/13/#cl-2)中科大源

deb <https://mirrors.ustc.edu.cn/ubuntu/> bionic main restricted universe multiverse\
deb <https://mirrors.ustc.edu.cn/ubuntu/> bionic-updates main restricted universe multiverse\
deb <https://mirrors.ustc.edu.cn/ubuntu/> bionic-backports main restricted universe multiverse\
deb <https://mirrors.ustc.edu.cn/ubuntu/> bionic-security main restricted universe multiverse\
deb <https://mirrors.ustc.edu.cn/ubuntu/> bionic-proposed main restricted universe multiverse\
deb-src <https://mirrors.ustc.edu.cn/ubuntu/> bionic main restricted universe multiverse\
deb-src <https://mirrors.ustc.edu.cn/ubuntu/> bionic-updates main restricted universe multiverse\
deb-src <https://mirrors.ustc.edu.cn/ubuntu/> bionic-backports main restricted universe multiverse\
deb-src <https://mirrors.ustc.edu.cn/ubuntu/> bionic-security main restricted universe multiverse\
deb-src <https://mirrors.ustc.edu.cn/ubuntu/> bionic-proposed main restricted universe multiverse\
完成更新源\
apt update

<!--EndFragment-->