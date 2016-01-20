---
layout: post
title: "linux-shell-cmd"
date: 2014-08-22 13:55
comments: true
categories: 
---

linux有些命令运维的时候经常会用到，没有及时整理，通过搜索复制粘贴又很容易忘记，所以整理了下。

###sed
* 替换文本中的某些字符，在自动化修改一些配置文件的时候可能会用到

{% highlight c%}
#将内容中的my替换成wikimo
$ sed -i "s/my/wikimo/g" pets.txt
{% endhighlight %}
* [参考文章](http://coolshell.cn/articles/9104.html)

###tail
* 一般用于查看系统日志

{% highlight c%}
#持续在命令行查看最新日志结果
tail -f file.log
{% endhighlight %}

{% highlight c%}
#查看最新一行日志信息
tail -n 1 file.log
{% endhighlight %}

###cut
* 剪切字符用，有些类似于程序中的strsub功能

{% highlight c%}
#以空格分割字符串，取第8个区域
cut -d' ' -f8
{% endhighlight %}

###awk

* 直接看[这里](http://coolshell.cn/articles/9070.html)已经描述的很清楚了

### ln

* 在编译安装程序的时候经常会用到，主要是一些类库的关联，source / target 注意不要搞错，一般常用ln -s 源文件（实际的文件） 目标文件


###管道|