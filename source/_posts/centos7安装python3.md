---
index_img: https://www.runoob.com/wp-content/uploads/2014/05/python3.png
title: centos7安装python3
date: 2022-09-19 10:15:26
updated: 2022-09-19 10:15:26
comments: true
---
<!--StartFragment-->

# CentOS系统

wget <https://www.moerats.com/usr/shell/Python3/CentOS_Python3.6.sh> && sh CentOS_Python3.6.sh

# [](https://c3.pw/index.php/archives/3/#cl-2)Debian系统

wget <https://www.moerats.com/usr/shell/Python3/Debian_Python3.6.sh> && sh Debian_Python3.6.sh\
输入Python命令，查看可以得知是Python2.7.5版本\
输入which python\
一般是位于/usr/bin/python目录下\
安装Python3\
首先安装依赖包\
yum -y groupinstall "Development tools"\
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel\
下载 Python3.6.2\
wget <https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tar.xz>\
新建文件夹，将软件放在python3下 mkdir /usr/local/python3\
然后解压压缩包，进入该目录，安装Python3\
tar -xvJf Python-3.6.2.tar.xz\
cd Python-3.6.2\
./configure --prefix=/usr/local/python3\
make -j && make install\
创建软链接\
ln -s /usr/local/python3/bin/python3 /usr/bin/python3\
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3

<!--EndFragment-->