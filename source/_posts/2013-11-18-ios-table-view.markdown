---
layout: post
title: "ios tableview学习"
date: 2013-11-18 20:38
comments: true
categories: 
---

找了一篇文章直接拿来练手了

* [iOS学习之Table View的简单使用](http://blog.csdn.net/totogo2010/article/details/7642908)

* [iOS-编写简单的TableView](http://disanji.net/2010/12/17/ios-design-simple-tableview/)

* [代码实现 UITableView与UITableViewCell](http://blog.csdn.net/duxinfeng2010/article/details/7724628)

说下上述例子的注意点，在利用xcode创建项目的时候，不勾选use automatic reference counting，不然对

{% highlight c %}
if(cell == nil)
{% endhighlight %}

做判断的时候通过release释放的时候会报错；

最后附上自己github的[demo](https://github.com/wikimo/TableViewDemo)