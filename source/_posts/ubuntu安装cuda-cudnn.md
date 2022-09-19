---
title: Ubuntu安装CUDA+CUDNN
date: 2022-09-19 10:10:41
updated: 2022-09-19 10:10:41
comments: true
---
<!--StartFragment-->

1.cuda的安装\
cuda下载地址 <https://developer.nvidia.com/cuda-downloads>

2.安装cuda\
以下步骤全都是ROOT权限操作\
chmod +x cuda_10.1.168_418.67_linux.run 将.run文件变成可执行文件\
./ cuda_10.1.168_418.67_linux.run\
运行安装cuda\
[![a](http://images5.10qianwan.com/10qianwan/20200731/b_0_202007310359113817.jpg "a")](http://images5.10qianwan.com/10qianwan/20200731/b_0_202007310359113817.jpg)\
选择安装cuda，这里我没有选择安装显卡驱动。有需要可以直接选择

安装完成

写入环境变量\
vim /etc/profile\
加入cuda环境变量\
export CUDA_HOME=/usr/local/cuda-10.1\
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.1/lib64\
export PATH=$PATH:/usr/local/cuda-10.1/bin\
export CUDA_HOME=$CUDA_HOME:/usr/local/cuda-10.1

保存退出后同步环境变量\
source /etc/profile\
nvcc -V\
验证cuda版本，有输出cuda版本，cuda安装成功。

3.cudnn的安装\
下载cudnn <https://developer.nvidia.com/rdp/cudnn-archive>\
下载完后解压，进入解压后的文件\
创建cuda的软连\
sudo cp cuda/include/* /usr/local/cuda/include/\
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/\
sudo chmod a+r /usr/local/cuda/include/cudnn.h\
sudo chmod a+r /usr/local/cuda/lib64/libcudnn*\
验证cudnn7安装是否成功\
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2\
验证cudnn8安装是否成功\
cat /usr/local/cuda/include/cudnn_version.h | grep CUDNN_MAJOR -A 2

CUDA+CUDNN 安装完成

<!--EndFragment-->