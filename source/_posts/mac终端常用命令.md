---
title: mac终端常用命令
id: 367
categories:
  - 未分类
date: 2016-07-14 16:58:33
tags:
---

清屏
{% codeblock lang:shell %}
clear | command + L
{% endcodeblock %}
显示所有进程
{% codeblock lang:shell %}
ps -A
{% endcodeblock %}
杀死进程
{% codeblock lang:shell %}
kill [-9] 进程号
{% endcodeblock %}
查看被占用的80端口（lsof:list open files）
{% codeblock lang:shell %}
sudo lsof -i :80 | grep -i "listen"
{% endcodeblock %}
查看在运行的程序
{% codeblock lang:shell %}
ps aux | grep amoeba
{% endcodeblock %}
查找文件
{% codeblock lang:shell %}
find 路径 -name '文件'
find / -name 'ljf'
{% endcodeblock %}
操作apache
{% codeblock lang:shell %}
# 重启apache
sudo /usr/sbin/apachectl restart
# 关闭apache
sudo /usr/sbin/apachectl stop
# 开启apache
sudo /usr/sbin/apachectl start
{% endcodeblock %}