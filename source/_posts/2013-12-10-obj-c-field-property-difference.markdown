---
layout: post
title: "object c的.h文件中字段和属性的区别"
date: 2013-12-10 14:41
comments: true
categories: 
---

刚开始一直没把这个问题搞明白，后来搜了下google，发现了答案[http://stackoverflow.com/questions/15811751/whats-the-difference-between-property-and-fields-in-objective-c](http://stackoverflow.com/questions/15811751/whats-the-difference-between-property-and-fields-in-objective-c)

里面写了这么一段话

With the second one you are only creating instance variables.
@property automatically generates you these as their associated getter and setter methods.

大概意思就是说，如果是写在{}大括号的字段，那么就只是实例变量，通过property方式，会给你自动生成get,set方法；