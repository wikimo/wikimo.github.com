---
layout: post
title: "reset-mysql-password"
date: 2015-01-30 13:23
comments: true
categories: mysql
---

做个记录，知道方法，老忘记具体的参数

{% highlight c%}
#安全模式运行mysql
mysqld_safe --skip-grant-tables --skip-networking & 

#无密码登陆mysql
mysql -u root  

#修改密码
use mysql;  
update user set password=PASSWORD("mynewpassword") where User='root';  
flush privileges;   
{% endhighlight %}

* [原文链接](http://www.ghostchina.com/how-to-reset-mysqls-root-password/)