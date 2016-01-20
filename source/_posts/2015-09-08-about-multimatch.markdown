---
layout: post
title: "about-multimatch"
date: 2015-09-08 00:05
comments: true
categories: js node
---

需要对bower下的js文件进行压缩，使用[main-bower-files](https://github.com/ck86/main-bower-files)这个库需要对文件进行filter，查看了文档，有filter参数可以做配置，跟踪源码后，发现使用了[multimatch](https://github.com/sindresorhus/multimatch)进行文件过滤，遇到一个需求是这样的，需要匹配当前bower_components下除了simditor关键词以外的文件。

{% highlight javascript %}
# ** 匹配所有文件；
# !**simditor**，排除simditor相关文件；
# !**/*simditor*/** 排除simditor相关目录；
['**', '!**simditor**', '!**/*simditor*/**']
{% endhighlight %}
