---
index_img: https://www.lammps.org/movies/logo.gif
title: lammps安装编译
date: 2022-09-19 10:09:57
updated: 2022-09-19 10:09:57
comments: true
---
<!--StartFragment-->

本所有编译都是在/OPT下面编译，共享目录\
1.下载fftw <http://www.fftw.org/fftw-3.3.8.tar.gz>\
2.下载mpich <http://www.mpich.org/static/downloads/3.3.2/mpich-3.3.2.tar.gz>\
3.下载lammps 选择第一个稳定版下载 <https://lammps.sandia.gov/download.html>

4.编译fftw

# [](https://c3.pw/index.php/archives/9/#cl-1)cd /opt

# [](https://c3.pw/index.php/archives/9/#cl-2)mkdir fftw3.3.8

# [](https://c3.pw/index.php/archives/9/#cl-3)wget <http://www.fftw.org/fftw-3.3.8.tar.gz>

# [](https://c3.pw/index.php/archives/9/#cl-4)tar -xvf fftw-3.3.8.tar.gz

# [](https://c3.pw/index.php/archives/9/#cl-5)cd fftw-3.3.8/

# [](https://c3.pw/index.php/archives/9/#cl-6)./configure --prefix=/opt/fftw3.3.8 --enable-shared=yes

# [](https://c3.pw/index.php/archives/9/#cl-7)make -j 4 && make install

5.编译mpich

# [](https://c3.pw/index.php/archives/9/#cl-8)cd /opt

# [](https://c3.pw/index.php/archives/9/#cl-9)mkdir mpich3.3.2

# [](https://c3.pw/index.php/archives/9/#cl-10)wget <http://www.mpich.org/static/downloads/3.3.2/mpich-3.3.2.tar.gz>

# [](https://c3.pw/index.php/archives/9/#cl-11)cd mpich-3.3.2

# [](https://c3.pw/index.php/archives/9/#cl-12)./configure --prefix=/opt/mpich3.3.2

# [](https://c3.pw/index.php/archives/9/#cl-13)make -j 4 && make install

6.编译lammps\
将下载好的lammps解压，进入文件内

# [](https://c3.pw/index.php/archives/9/#cl-14)cd /opt/lammps-3Mar20/src/MAKE

# [](https://c3.pw/index.php/archives/9/#cl-15)vim Makefile.mpi

将下面一行注释，如图\
[![修改](https://img.maocdn.cn/img/2020/12/02/16068961641.png "修改")](https://img.maocdn.cn/img/2020/12/02/16068961641.png)

# [](https://c3.pw/index.php/archives/9/#cl-16)LMP_INC = -DLAMMPS_GZIP -DLAMMPS_MEMALIGN=64 # -DLAMMPS_CXX98

修改保存退出

# [](https://c3.pw/index.php/archives/9/#cl-17)cd ../src

加入模块

# [](https://c3.pw/index.php/archives/9/#cl-18)make package-status //查看lammps可用模块

# [](https://c3.pw/index.php/archives/9/#cl-19)make yes-all

# [](https://c3.pw/index.php/archives/9/#cl-20)make no-lib

# [](https://c3.pw/index.php/archives/9/#cl-21)make no-ext

# [](https://c3.pw/index.php/archives/9/#cl-22)make -j 4 mpi

环境变量\
export PATH=/opt/mpich3.3.2/bin:/opt/fftw3.3.8/bin:/opt/lammps-3Mar20/src:$PATH\
export LD_LIBRARY_PATH=/opt/fftw3.3.8/lib:/opt/mpich3.3.2/lib:$LD_LIBRARY_PATH\
以上就全部编译完成\
------分割--------\
然后进入算例mpirun -np 8 lmp_mpi < in.friction\
算例正常运行\
如果需要安装gpu版\
cd /opt/lammps-3Mar20/lib/gpu\
vim Makefile.linux\
CUDA_HOME=/usr/local/cuda-11.1\
下面参数修改请看**[CUDA](https://en.wikipedia.org/wiki/CUDA#GPUs_supported)**维基百科

[![1667718797718.jpg](https://s2.232232.xyz/static/266/2022/11/06-63675f6d174b1.jpg)](https://s2.232232.xyz/static/266/2022/11/06-63675f6d174b1.jpg)

# [](https://c3.pw/index.php/archives/9/#cl-23)Turing hardware

CUDA_ARCH = -arch=sm_75\
修改完成保存退出\
make -f Makefile.linux\
cd /opt/lammps-3Mar20/src\
make yes-gpu\
make -j mpi\
计算12核加gpu\
mpirun -np 12 lmp_mpi -sf gpu -pk gpu 1 -in in.friction

关于编译lammps+plumed\
需下载lammps-stable_7Aug2019的版本\
cd src\
make lib-plumed args="-b"\
make yes-all\
make no-lib\
make no-ext\
make yes-plumed或make yes-user-plumed\
make -j 8 mpi

<!--EndFragment-->