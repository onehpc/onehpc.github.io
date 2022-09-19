---
title: 大气软件WRF安装和WPS安装
date: 2022-09-19 10:06:14
updated: 2022-09-19 10:06:14
comments: true
---
<!--StartFragment-->

Ubuntu系统编译\
已编译好的WRF和WPS\
链接：<https://pan.baidu.com/s/1oADC7_YuxBKaP7fdqa3ggg>\
提取码：x35x\
傻瓜式安装已编译好的\
将下载好wrf4.1.2.tar.gz拷贝/opt下面\
tar -xvf wrf4.1.2.tar.gz\
cd /opt/Build_WRF/WRF-4.1.2/main\
ls -ls *.exe\
WRF和WPS 都已经编译完成

写本机的环境变量\
将WRF未编译版文档文件夹下profile环境变量，复制进自己环境变量里面就行\
以下未编译版教程和所需环境包\
链接：<https://pan.baidu.com/s/1OnATznTd_goXdPcYnO9Isw>\
提取码：pq1u\
查看本机环境和安装依赖包\
which gfortran\
which cpp\
which gcc g++\
apt install csh\
apt-get install m4\
apt install gfortran\
apt install g++\
apt install make\
apt install make-guile\
gcc --version\
将WRF未编译版文档文件下Build_WRF上传/opt\
1.NetCDF:\
vi ~/.bashrc （更改环境变量，可将WRF未编译版文档的文件下的profile，复制到自己的环境变量里面）\
（更改环境变量可以和后面的一口气改完，每次修改后都需要输入【source ~/.bashrc】使修改的环境变量生效）\
a（启动修改）

# [](https://c3.pw/index.php/archives/15/#cl-1)netcdf

export DIR=path_to_directory/Build_WRF/LIBRARIES\
（此处为LIBRARIES的路径，输入刚才pwd查看到的路径）\
export CC=gcc\
export CXX=g++\
export FC=gfortran\
export FCFLAGS=-m64\
export F77=gfortran\
export FFLAGS=-m64\
按下Esc，再输入:wq(保存退出)\
source ~/.bashrc(使修改的环境变量生效)\
tar xzvf netcdf-4.1.3.tar.gz(解压)\
cd netcdf-4.1.3\
./configure --prefix=$DIR/netcdf --disable-dap --disable-netcdf-4 --disable-shared\
make-j\
make install\
vi ~/.bashrc （更改环境变量）\
a（启动修改）

# [](https://c3.pw/index.php/archives/15/#cl-2)netcdf

export PATH=$DIR/netcdf/bin:$PATH\
export NETCDF=$DIR/netcdf\
按下Esc，再输入:wq(保存退出)\
source ~/.bashrc(使修改的环境变量生效)\
cd ..（打开上一级）\
2.mpich\
tar xzvf mpich-3.0.4.tar.gz\
cd mpich-3.0.4\
./configure --prefix=$DIR/mpich\
make -j\
make install\
vi ~/.bashrc （更改环境变量）\
a（启动修改）

# [](https://c3.pw/index.php/archives/15/#cl-3)mpich

export PATH=$DIR/mpich/bin:$PATH\
按下Esc，再输入:wq(保存退出)\
source ~/.bashrc(使修改的环境变量生效)\
cd ..（打开上一级）

3. zlib:\
   vi ~/.bashrc （更改环境变量）\
   a（启动修改）

   # [](https://c3.pw/index.php/archives/15/#cl-4)zlib

   export LDFLAGS=-L$DIR/grib2/lib\
   export CPPFLAGS=-I$DIR/grib2/include\
   按下Esc，再输入:wq(保存退出)\
   source ~/.bashrc(使修改的环境变量生效)\
   tar xzvf zlib-1.2.7.tar.gz\
   cd zlib-1.2.7\
   ./configure --prefix=$DIR/grib2\
   make -j\
   make install\
   cd .. （打开上一级）
4. libpng:\
   tar xzvf libpng-1.2.50.tar.gz\
   cd libpng-1.2.50\
   ./configure --prefix=$DIR/grib2\
   make -j\
   make install\
   cd ..
5. JasPer:\
   tar xzvf jasper-1.900.1.tar.gz\
   cd jasper-1.900.1\
   ./configure --prefix=$DIR/grib2\
   make -j\
   make install\
   cd ..\
   Library Compatibility Tests\
   省略\
   Building WRFV3\
   cd .. （打开上一级）\
   pwd（查看此时目录）\
   ls（查看当前目录下文件）\
   （上传WPS和WRF安装包）\
   tar xzvf WRF-4.1.2.tar.gz\
   cd WRF-4.1.2\
   ./configure\
   34(这里我是在集群计算机上安装所以选的34，自己的电脑可以选32或33)\
   1\
   ./compile em_real >& log.compile\
   ls -ls main/*.exe\
   (出现4个exe安装成功)\
   cd ..\
   Building WPS\
   tar xzvf WPS-4.1.tar.gz\
   cd WPS-4.1\
   ./clean\
   vi ~/.bashrc （更改环境变量）\
   a（启动修改）

   # [](https://c3.pw/index.php/archives/15/#cl-5)WPS

   export JASPERLIB=$DIR/grib2/lib\
   export JASPERINC=$DIR/grib2/include\
   export WRF_DIR = ../ WRF-4.1.2\
   按下Esc，再输入:wq(保存退出)\
   source ~/.bashrc(使修改的环境变量生效)\
   ./configure\
   1(和WRF一致)\
   ./compile >& log.compile\
   ls -ls *.exe\
   (出现3个exe即为成功，我的一般是2个缺少ungrib，需要进一步解决，问题和解决办法在<http://www2.mmm.ucar.edu/wrf/users/wpsv3.9/known-prob-3.9.html>，可以直接用我改好的read_namelist.F，替换掉文件夹…/ WPS-4.1/ungrib/src下的read_namelist.F\
   ./compile >& log.compile（重新编译）\
   ls -ls *.exe\
   WRF和WPS环境变量\
   export PATH=/opt/Build_WRF/WRF-4.1.2/main:$PATH\
   export PATH=/opt/Build_WRF/WPS-4.1:$PATH\
   完成！

<!--EndFragment-->