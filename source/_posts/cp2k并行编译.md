---
title: CP2K并行编译
date: 2022-09-19 10:12:18
updated: 2022-09-19 10:12:18
comments: true
---
<!--StartFragment-->

下载源码包此处为cp2k6.1，本文编译方法和 cp2k 7.1通用，cp2k7.1安装时所需依赖包都是从github下载，比较慢，也容易下载出错，cp2k6.1没有这种情况。

# [](https://c3.pw/index.php/archives/7/#cl-1)cd /opt

# [](https://c3.pw/index.php/archives/7/#cl-2)wget <https://github.com/cp2k/cp2k/releases/download/v6.1.0/cp2k-6.1.tar.bz2>

解压cp2k

# [](https://c3.pw/index.php/archives/7/#cl-3)tar -xvf cp2k-6.1.tar.bz2

安装cp2k

# [](https://c3.pw/index.php/archives/7/#cl-4)cd /opt/cp2k-6.1/tools/toolchain

# [](https://c3.pw/index.php/archives/7/#cl-5)./install_cp2k_toolchain.sh

如果有报错可能mpich的环境冲突，在线安装mpich

# [](https://c3.pw/index.php/archives/7/#cl-6)yum install mpich-*

安装完成后出现以下\
Now copy:\
cp /opt/cp2k-6.1/tools/toolchain/install/arch/* to the cp2k/arch/ directory\
To use the installed tools and libraries and cp2k version\
compiled with it you will first need to execute at the prompt:\
source /opt/cp2k-6.1/tools/toolchain/install/setup\
To build CP2K you should change directory:\
cd cp2k/makefiles/\
make -j 8 ARCH=local VERSION="sopt sdbg ssmp popt pdbg psmp"\
按照提示安装\
cp -r /opt/cp2k-6.1/tools/toolchain/install/arch/ /opt/cp2k-6.1/arch/\
source /opt/cp2k-6.1/tools/toolchain/install/setup\
cd /opt/ cp2k-6.1/makefiles/\
make -j 8 ARCH=local VERSION= "popt "\
等待编译安装完成\
生成的文件在/opt/cp2k-6.1/exe/local\
cp2k.popt 这个就是生成可执行文件\
添加环境变量

# [](https://c3.pw/index.php/archives/7/#cl-7)export PATH=/opt/cp2k-6.1/exe/local:$PATH

测试算例

# [](https://c3.pw/index.php/archives/7/#cl-8)cd /opt/cp2k-6.1/tests/FE/regtest-1

# [](https://c3.pw/index.php/archives/7/#cl-9)mpirun -np 8 cp2k.popt Solv_alch_chng.inp

<!--EndFragment-->