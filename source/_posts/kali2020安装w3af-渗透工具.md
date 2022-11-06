---
index_img: https://image.3001.net/images/20170904/15045054202931.png
title: kali2020安装w3af 渗透工具
date: 2022-09-19 10:11:30
updated: 2022-09-19 10:11:30
comments: true
---
<!--StartFragment-->

关于w3af是什么可以GitHub上的描述文件\
开源地址<https://github.com/andresriancho/w3af>\
w3af-Web应用程序攻击和审核框架\
w3af是一个开放源代码 Web应用程序安全扫描程序，可帮助开发人员和渗透测试人员识别和利用其Web应用程序中的漏洞。\
该扫描程序能够识别200多个漏洞，包括跨站点脚本， SQL注入和 OS命令。

安装开始\
老规矩先git

```

```

完成后在修改一下配置文件，我用的是kali2020这里必须修改，不然后面一直会卡在python-pip那里，因为kali的源里面没办法apt安装。\
进入git好的目录下面

```

```

34行python-pip删除，然后保存退出。\
在w3af目录下运行

```

```

根据提示进入tmp

```

```

然后修改要安装的内容，不然有报错，删除bravado-core==5.15.0，在运行

```

```

安装pyrsistent可能会出错，原因是已经有高版本的，需将高版本的用pip删除的在进行安装

```

```

安装完成后，在进入w3af\
`./w3af_console./w3af_console` 这个会直接进入控制台

/usr/share/offsec-awae-wheels/pyOpenSSL-19.1.0-py2.py3-none-any.whl/OpenSSL/crypto.py:12: CryptographyDeprecationWarning: Python 2 is no longer supported by the Python core team. Support for it is now deprecated in cryptography, and will be removed in the next release.\
w3af>>>

不懂话可以先运行

```

```

/usr/share/offsec-awae-wheels/pyOpenSSL-19.1.0-py2.py3-none-any.whl/OpenSSL/crypto.py:12: CryptographyDeprecationWarning: Python 2 is no longer supported by the Python core team. Support for it is now deprecated in cryptography, and will be removed in the next release.

w3af - Web Application Attack and Audit Framework

Usage:

```

```

Options:

```

```

For more info visit <http://w3af.org/>\
安装成功展示

<!--EndFragment-->