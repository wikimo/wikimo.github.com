---
layout: post
title: "关于tomcat jdbc driver 内存泄露问题"
date: 2013-05-16 12:07
comments: true
categories: 
---


在tomcat运行某个项目的时候，可能会碰到以下问题

 The web application [] registered the JDBC driver [com.mysql.jdbc.Driver] but failed to unregister it when the web application was stopped. To prevent a memory leak, the JDBC Driver has been forcibly unregistered.

大致翻译如下：应用程序注册了JDBC驱动，但当程序停止时无法注销这个驱动，tomcat为了防止内存溢出，就给强制注销了。

查阅了很多资料，大概原因是因为tomcat6开始的某些版本加入了内存泄露检测。对于此问题的解法大致有以下几种：

 1.tomcat配置文件注释掉内存泄露监听；

 2.配置tomcat 内存启动参数；

 3.重写datasource类中的相关方法；（经检验，此方法最靠谱）


#### 重写datasource示例：

{% highlight java%}
public class XBasicDataSource extends BasicDataSource {
    @Override
    public synchronized void close() throws SQLException {
        DriverManager.deregisterDriver(DriverManager.getDriver(url));
        super.close();
    }
}
{% endhighlight %}

如果使用了spring，可在spring applicationContext.xml，将数据源指向自定义的类。


####另可能涉及的一些jar 

common-pool.jar ，common-dhcp.jar


#### 参考资源：
[http://blog.csdn.net/nihao0526/article/details/7246353](http://blog.csdn.net/nihao0526/article/details/7246353)

[https://issues.apache.org/jira/browse/DBCP-332](https://issues.apache.org/jira/browse/DBCP-332)