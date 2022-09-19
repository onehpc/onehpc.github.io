---
title: CentOS下查看并杀死僵尸进程
date: 2022-09-19 09:59:03
updated: 2022-09-19 09:59:03
comments: true
---
<!--StartFragment-->

先用top命令查看有没有僵尸程序\
有的话使用一键命令kill掉\
`ps -A -o stat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}' | xargs kill -9`

<!--EndFragment-->