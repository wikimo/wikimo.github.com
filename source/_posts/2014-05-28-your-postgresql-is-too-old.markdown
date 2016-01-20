---
layout: post
title: "Your PostgreSQL is too old."
date: 2014-05-28 15:01
comments: true
categories: 
---

问题描述：在通过gem安装pg时会抱这个错误

解法：

* 可能是pg的安装路径问题，需要自己去指定，类似这样
{% highlight c %}
gem install pg -- --with-pgsql-lib=/usr/pgsql-9.3/lib --with-pg-config=/usr/pgsql-9.3/bin/pg_config
{% endhighlight %}
* 如果上述安装报错，找相应的错误日志，gem_make.out，mkmf.log这些文件，命令行会给出这些文件的路径在哪，然后去分析问题，可能得到的结果是：undefined reference to PQconnectionUsedPassword。可能是postgresql对于的开发包(devel)没有安装导致的，Centos下解法是：
{% highlight c %}
yum install postgresql93-contrib postgresql93-devel
{% endhighlight %}