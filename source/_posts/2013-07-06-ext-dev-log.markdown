---
layout: post
title: "ExtJS常见错误汇总"
date: 2013-07-06 11:07
comments: true
categories: 
---

之前有个面向企业级的项目，对于UI部分纠结了蛮久，看了很多UI框架。比如：EasyUI，dwz，LigerUI，miniui，Extjs。最终还是选择了Extjs，上手之后，编码相对来说还是比较轻松的，其中碰到的一些问题整理了下。

#### 1.TypeError: this.addEvents is not a function

由于其中的一个控件没有使用关键字new出来或使用关键字new来创建时出错
http://techpool.iteye.com/blog/480890 

#### 2.this.config[col] is undefined

在Grid定义的时候对某列使用了autoExpandColumn属性，而这个属性所指定的是某列定义的id属性,该列上没有指定id,所以出错了
http://cst.is-programmer.com/posts/22711.html 

#### 3.extjs radiogroup无法取值问题

因为ExtJs地RadioGroup中没有实现getValue这个方法
http://www.yyjjssnn.cn/articles/450.html


#### 4.extjs radiogroup 通过window方式调用有滚动条问题

通过设置radio autoWidth:true, height:30;

#### 5.格式化货币符号问题。

通过Ext.util.Format可以自行扩展，format下可以扩展很多自定义的方法，比如根据类型显示性别。可以扩展Ext.util.Format.sex这样的方法