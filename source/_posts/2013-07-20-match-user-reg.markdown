---
layout: post
title: "ruby 匹配@艾特用户名"
date: 2013-07-20 10:22
comments: true
categories: 
---

需要通过利用@符进行消息通知的功能，前端可以通过atWho插件解决，后端需要去解析字符串，研究了ruby-china源码，发现对中文用户名匹配似乎不太友好，于是找了资料改进了下，仅供参考。

{% highlight ruby%}
# coding: utf-8
#正则用于匹配用户名
str = "@wikimo @中國 @水手   测试看看"

#{2,20}字符长度至少2个，不多于20个，以下任意方式匹配
#arr = str.scan(/@([一-龠\w]{2,20}\s)/u).flatten
arr = str.scan(/@([\p{Han}+\w]{2,20}\s)/u).flatten

puts arr
{% endhighlight %}

参考资料： 

[http://ruby-china.org/topics/5680](http://ruby-china.org/topics/5680) 

ruby-china 源码