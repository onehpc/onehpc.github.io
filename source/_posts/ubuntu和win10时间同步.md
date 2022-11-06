---
index_img: https://photos.kzwr.com/files/230f9cb1081d4e86ab54ab804582c846tp4q.jpeg
title: ubuntu和win10时间同步
date: 2022-09-19 10:03:57
updated: 2022-09-19 10:03:57
comments: true
---
<!--StartFragment-->

1.安装ntpdate：\
`sudo apt-get install ntpdate`\
2.设置校正服务器：\
`sudo ntpdate time.windows.com`\
3.设置硬件时间为本地时间：\
`sudo hwclock --localtime --systohc`

<!--EndFragment-->