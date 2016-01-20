---
layout: post
title: "在OS X下安装MySQL-python"
date: 2013-11-26 20:45
comments: true
categories: 
---

在OS X安装MySQL-python尝试了很多方法，
* 通过python install;
* easy_install;
* pip install;
等这些方法，基本都在_mysql.c大概在1563行左右卡主

{% highlight c %}
	if (how < 0 || how >= sizeof(row_converters)) {
		PyErr_SetString(PyExc_ValueError, "how out of range");
		return NULL;
	}
{% endhighlight %}

搜了很多方法，都解决不了，最后通过

{% highlight c %}
sudo ARCHFLAGS='-arch x86_64' python setup.py build
sudo ARCHFLAGS='-arch x86_64' python setup.py install
{% endhighlight %}

解决了。

补充：通过MysqlDB-python安装包去安装，可能会碰到以下问题

关于_mysql.c:602: error: expected expression before ‘)’ token 的问题

主要是
{% highlight c %}
	&local_infile,
#ifdef HAVE_MYSQL_OPT_READ_TIMEOUT
	&read_timeout
#endif
{% endhighlight %}

在判断的时候，需要把前一个逗号放到if判断中去，类似这样

{% highlight c %}
	&local_infile
#ifdef HAVE_MYSQL_OPT_READ_TIMEOUT
	,&read_timeout
#endif
{% endhighlight %}

修改下_mysql.c源码就可以了。