---
title: ubuntu安装OpenFOAM
date: 2022-11-17 17:07:16
updated: 2022-11-17 17:07:16
comments: true
---
<!--markdown-->系统为Ubuntu18.04系统

开始
#sudo apt update
#sudo apt-get install build-essential flex bison git-core cmake zlib1g-dev libboost-system-dev libboost-thread-dev libopenmpi-dev openmpi-bin gnuplot libreadline-dev libncurses-dev libxt-dev -y
#sudo apt-get install qt4-dev-tools libqt4-dev libqt4-opengl-dev freeglut3-dev libqtwebkit-dev -y
在home用户的目录下面建 OpenFOAM9 文件夹
#mkdir /home/Users/ OpenFOAM9
#cd /home/Users/ OpenFOAM9
在 OpenFOAM 7 文件下面下载源码包
下面是加速下载链接
#git clone https://github.91chi.fun/https://github.com/OpenFOAM/OpenFOAM-9.git
#git clone https://github.91chi.fun/https://github.com/OpenFOAM/ThirdParty-9.git
原github下载链接
#git clone https://github.com/OpenFOAM/OpenFOAM-9.git
#git clone https://github.com/OpenFOAM/ThirdParty-9.git
#source $HOME/OpenFOAM7/OpenFOAM-7/etc/bashrc
编译此处为全核编译，编译时间较长
以下16是设置核数
export WM_NCOMPPROCS=  ##指定使用服务器用来编译的核数
export WM_NCOMPPROCS=16
export WM_COLOURS="black blue green cyan red magenta yellow"
#./Allwmake -j
编译完成后测试输出，出现以下的输出的，编译成功
#blockMesh