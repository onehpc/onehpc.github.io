---
index_img: https://blog.z0ukun.com/wp-content/uploads/2019/12/8720113544669.png
title: 宝塔面板安装zabbix V3.0
date: 2022-09-19 10:07:48
updated: 2022-09-19 10:07:48
comments: true
---
<!--StartFragment-->

第一步宝塔面板安装\
Centos安装命令：\
yum install -y wget && wget -O install.sh <http://download.bt.cn/install/install_6.0.sh> && sh install.sh\
Ubuntu/Deepin安装命令：\
wget -O install.sh <http://download.bt.cn/install/install-ubuntu_6.0.sh> && sudo bash install.sh\
Debian安装命令：\
wget -O install.sh <http://download.bt.cn/install/install-ubuntu_6.0.sh> && bash install.sh\
Fedora\
wget -O install.sh <http://download.bt.cn/install/install_6.0.sh> && bash install.sh\
安装宝塔面板后一键部署 lnmp环境\
PHP版本必须为5.6\
数据库名称必须是zabbix\
安装zabbix\
进入你网站的路径，比如我的：cd /www/wwwroot/zabbix.icunity.com\
wget <http://www.tieww.com/soft/zabbix.sh>\
sh zabbix.sh\
这个在线安装很慢，建议先上传zabbix安装包，然后在执行sh zabbix.sh\
zabbix安装包网盘： <https://www.lanzous.com/i4aa5wb>\
Enter zabbix database password:\
输入你创建数据库时的密码\
进入宝塔面板数据库复制zabbix粘贴数据密码 回车键\
zabbix site directory, for example (/www/default):

输入你网站的路径，比如我的 /www/wwwroot/zabbix.icunity.com 回车键\
耐心等待安装完成即可。安装成功会提示：\
Starting zabbix_server: \[ OK ]\
Starting zabbix_agentd: \[ OK ]\
Prompt:　zabbix installed successfully.\
进入宝塔面板软件商店修改php5.6配置\
[![a](https://img.maocdn.cn/img/2020/12/02/a.png "a")](https://img.maocdn.cn/img/2020/12/02/a.png)\
将此处修改为300\
[![b](https://img.maocdn.cn/img/2020/12/02/b.png "b")](https://img.maocdn.cn/img/2020/12/02/b.png)\
此处将702行的前面冒号删除\
进入网站或者ip地址\
配置数据库信息 database port 填写：3306 password 填写数据库的密码\
下一步 安装完成\
修改web界面为中文\
[![c](https://img.maocdn.cn/img/2020/12/02/c.png "c")](https://img.maocdn.cn/img/2020/12/02/c.png)\
/www/wwwroot/你的域名/include/locales.inc.php\
将此处改为true\
从Windows系统上的C:\Windows\Fonts目录中复制一个中文字体文件\
字体包网盘： <https://www.lanzous.com/i4aa5od>\
把字体文件msyh.ttf上传到zabbix站点根目录下fonts文件夹中\
例如：/www/wwwroot/zabbix.icunity.com/fonts\
备份默认的字体文件：DejaVusSans.ttf-bak\
修改msyh.ttf名称为DejaVusSans.ttf\
最后进入网站或者ip，个人中心修改配置信息，把默认语言修改为中文\
Language：Chinese（zh_CN）\
测试站 zabbix.icunity.com 安装好后的帐号：admin 密码：zabbix\
启动zabbix3.0\
点击主机 默认是关闭状态，选择启用

<!--EndFragment-->