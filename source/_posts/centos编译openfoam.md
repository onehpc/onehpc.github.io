---
title: centos编译openfoam
date: 2022-09-19 10:14:42
updated: 2022-09-19 10:14:42
comments: true
---
<!--StartFragment-->

先安装openmpi安装\
yum install libxml2-devel libxslt-devel gsl -y\
yum install openssl -y\
yum install openssl-devel -y

# [](https://c3.pw/index.php/archives/6/#cl-1)mkdir /opt/openmpi

# [](https://c3.pw/index.php/archives/6/#cl-2)cd /opt/openmpi

# [](https://c3.pw/index.php/archives/6/#cl-3)wget <https://download.open-mpi.org/release/open-mpi/v4.0/openmpi-4.0.4.tar.gz>

# [](https://c3.pw/index.php/archives/6/#cl-4)tar -xvf openmpi-4.0.4.tar.gz

# [](https://c3.pw/index.php/archives/6/#cl-5)cd openmpi-4.0.0

# [](https://c3.pw/index.php/archives/6/#cl-6)./configure --prefix=/opt/openmpi

# [](https://c3.pw/index.php/archives/6/#cl-7)make -j && make install

加入环境变量

# [](https://c3.pw/index.php/archives/6/#cl-8)export PATH=/opt/openmpi/bin:$PATH

# [](https://c3.pw/index.php/archives/6/#cl-9)export LD_LIBRARY_PATH=/opt/openmpi/lib:$LD_LIBRARY_PATH

接下来编译openfoam，编译最新openfoam8

# [](https://c3.pw/index.php/archives/6/#cl-10)mkdir /opt/openfoam

# [](https://c3.pw/index.php/archives/6/#cl-11)cd /opt/openfoam

# [](https://c3.pw/index.php/archives/6/#cl-12)wget -O - <http://dl.openfoam.org/source/8> | tar xvz

# [](https://c3.pw/index.php/archives/6/#cl-13)wget -O - <http://dl.openfoam.org/third-party/8> | tar xvz

# [](https://c3.pw/index.php/archives/6/#cl-14)mv OpenFOAM-8-version-8 OpenFOAM-8

# [](https://c3.pw/index.php/archives/6/#cl-15)mv ThirdParty-8-version-8 ThirdParty-8

# [](https://c3.pw/index.php/archives/6/#cl-16)cd /opt/openfoam/OpenFOAM-8

# [](https://c3.pw/index.php/archives/6/#cl-17)source /opt/openfoam/OpenFOAM-8/etc/bashrc

这步同步成功无报错就可以下一步\
以下16是设置核数\
export WM_NCOMPPROCS= ##指定使用服务器用来编译的核数\
export WM_NCOMPPROCS=16\
export WM_COLOURS="black blue green cyan red magenta yellow"

# [](https://c3.pw/index.php/archives/6/#cl-18)./Allwmake -j

编译时间较长\
如source同步出错，请按照下列操作临时升级gcc 此处为7.3版本

# [](https://c3.pw/index.php/archives/6/#cl-19)yum -y install centos-release-scl

# [](https://c3.pw/index.php/archives/6/#cl-20)yum -y install devtoolset-7-gcc devtoolset-7-gcc-c++ devtoolset-7-binutils

# [](https://c3.pw/index.php/archives/6/#cl-21)scl enable devtoolset-7 bash

需要注意的是scl命令启用只是临时的，退出shell或重启就会恢复原系统gcc版本。\
如果要长期使用gcc 7.3的话：\
echo "source /opt/rh/devtoolset-7/enable" >>/etc/profile\
如编译时出错安装编译zlib库

# [](https://c3.pw/index.php/archives/6/#cl-22)cd /opt/ openfoam/

# [](https://c3.pw/index.php/archives/6/#cl-23)wget <http://www.zlib.net/zlib-1.2.11.tar.gz>

# [](https://c3.pw/index.php/archives/6/#cl-24)tar zxvf zlib-1.2.11.tar.gz

# [](https://c3.pw/index.php/archives/6/#cl-25)cd zlib-1.2.11

# [](https://c3.pw/index.php/archives/6/#cl-26)./configure

# [](https://c3.pw/index.php/archives/6/#cl-27)make test

# [](https://c3.pw/index.php/archives/6/#cl-28)make install

构建共享库

# [](https://c3.pw/index.php/archives/6/#cl-29)make clean

# [](https://c3.pw/index.php/archives/6/#cl-30)./configure --shared

make test\
make install\
cp zutil.h /usr/local/include\
cp zutil.c /usr/local/include\
将zlib库安装成后继续编译\
编译完成后测试输出，出现以下的输出的，编译成功

# [](https://c3.pw/index.php/archives/6/#cl-31)blockMesh

[![of7](http://image.sciencenet.cn/home/201903/13/141912oedzffkd4pdo7qfd.png "of7")](http://image.sciencenet.cn/home/201903/13/141912oedzffkd4pdo7qfd.png)

<!--EndFragment-->