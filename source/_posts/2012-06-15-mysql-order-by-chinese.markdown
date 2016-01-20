---
layout: post
title: "mysql汉字拼音排序测试"
date: 2012-06-15 21:41
comments: true
categories: database
---

关于mysql汉字拼音排序的一些测试，网上搜了一些相关的资料，同时自己也做了下简单的测试，UTF8编码未做测试，只测了GBK，GBK下，其实直接order by 就可以了，但是涉及英文字母的时候，不会和中文间隔排序，但基本也满足我需求了，不用排序很精准，仅供参考。

{% highlight sql %}
-- create table
CREATE TABLE IF NOT EXISTS `test` (
  `id` smallint(5) NOT NULL AUTO_INCREMENT,
  `username` varchar(25) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB  DEFAULT CHARSET=gbk AUTO_INCREMENT=1 ;

-- insert
insert into test(username) values('张三'),('李斯'),('王五'),('马六'),('钱起'),('wikimo'),('james'),('lucy');

-- select data
SELECT  *  FROM  test   ORDER BY CONVERT( username USING gbk ) COLLATE gbk_chinese_ci ASC; 

select  *  from test order by username asc;
{% endhighlight %}

参考资料：
[http://stanlyy.iteye.com/blog/654834](http://stanlyy.iteye.com/blog/654834)
[http://hi.baidu.com/java513/item/91c715c288a894330831c63a](http://hi.baidu.com/java513/item/91c715c288a894330831c63a)