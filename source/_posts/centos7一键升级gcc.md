---
index_img: https://i.w3tt.com/2021/08/17/q9m8S.png
title: centos7一键升级gcc
date: 2022-09-19 10:05:29
updated: 2022-09-19 10:05:29
comments: true
---
<!--StartFragment-->

yum -y install centos-release-scl\
yum -y install devtoolset-7-gcc devtoolset-7-gcc-c++ devtoolset-7-binutils\
临时使用gcc-7\
scl enable devtoolset-7 bash\
长期使用\
echo "source /opt/rh/devtoolset-7/enable" >>/etc/profile\
下面是源码编译gcc\
先yum下载依赖包\
yum install libgcc.i686 glibc-devel.i686 flex gcc-gfortran libstdc++ glibc libgcc libc6-dev libc6-devel glibc-devel qt4-devel curl-devel gcc glibc-devel2 -y\
gcc源码包地址：<https://ftp.gnu.org/gnu/gcc/>\
我用的是gcc8.3源码编译，理论来说这个编译方法可以适用其他版本gcc\
1、下载\
下载速度不一，请选择速度最快的：\
<https://mirrors.nju.edu.cn/gnu/gcc/gcc-9.1.0/>\
tar -zxvf gcc-9.1.0.tar.gz\
cd gcc-9.1.0\
./contrib/download_prerequisites\
由于网络问题下载可会出错，我这提供gcc下载依赖包<https://icunity.lanzoui.com/ikC7Lskl5mb>\
将gmp-6.1.0.tar.bz2，isl-0.18.tar.bz2，mpc-1.0.3.tar.gz，mpfr-3.1.4.tar.bz2放在gcc-8.3.0的目录下面\
./contrib/download_prerequisites\
[![qfD9L.png](https://i.w3tt.com/2021/08/13/qfD9L.png "qfD9L.png")](https://i.w3tt.com/2021/08/13/qfD9L.png)\
这里全部ok的话操作下面步骤，然后编译\
只升级gcc\
./configure --prefix=/opt/gcc8.3 --enable-multilib --enable-languages=c,c++
只升级gcc和fortran 建议这个
./configure --prefix=/opt/gcc8.3 --enable-multilib --enable-languages=c,c++,fortran
make 漫长的等待, 建议使用make，不要用make -j，make -j有可能会编译出错\
make install\
安装完成\
[![q9m8S.png](https://i.w3tt.com/2021/08/17/q9m8S.png "q9m8S.png")](https://i.w3tt.com/2021/08/17/q9m8S.png)

<!--EndFragment-->