---
layout: post
title: "linux contains a file system with errors"
date: 2012-09-03 09:09
comments: true
categories: 
---

现象：linux无法启动，提示磁盘有错误，需要检查磁盘，磁盘自检一段时间后会卡住或者自动重启，提示信息可能为"contains a file system with errors,check forced"之类的。后面会提示是否用过管理员密码进入命令行。

解决方案：通过提示进入命令行，然后通过fsck.ext3进行修复。

{% highlight c%}
#具体是sda几可以通过tab键来补全，不行的话，都可以试试
fsck.ext3 -y /dev/sda
{% endhighlight %}

等执行完毕后，重启基本就OK了，碰见过两次，屡试不爽。