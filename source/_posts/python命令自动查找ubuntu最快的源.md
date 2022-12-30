---
title: python命令自动查找ubuntu最快的源
date: 2022-12-30 08:54:18
updated: 2022-12-30 08:54:18
comments: true
---
<!--StartFragment-->

Ubuntu系统是最受欢迎的Linux发行版之一这里介绍一种在命令行下自动换最快源的方法。

<!--EndFragment-->

<!--StartFragment-->

1. sudo apt install python3-pip python3-setuptools python3-wheel
2. pip3 install apt-smart

<!--EndFragment-->

<!--StartFragment-->

这样就安装好了自动换源的python脚本apt-smart，该脚本的使用方法很简单：

<!--EndFragment-->

<!--StartFragment-->

1. 要列出最快的源:
2. apt-smart -l
3. 要应用最快的源：
4. apt-smart -a

<!--EndFragment-->