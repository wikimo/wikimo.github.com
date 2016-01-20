---
layout: post
title: "linux安装软件时常用命令"
date: 2014-01-27 13:12
comments: true
categories: 
---

* 查询某个程序对于lib的依赖，可用ldd命令
{% highlight c%}
#查看nginx的依赖库，是不是少了哪个lib
ldd /usr/local/webserver/nginx/sbin/nginx 
{% endhighlight %}

* 查看lib 链接指向
{% highlight c%}
ls -l file_name
{% endhighlight %}

* 建立软链接
{% highlight c%}
ln -s source_file target_file
{% endhighlight %}