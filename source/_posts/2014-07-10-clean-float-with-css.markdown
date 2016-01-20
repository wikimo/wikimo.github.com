---
layout: post
title: "clean-float-with-css"
date: 2014-07-10 14:18
comments: true
categories: 
---

css to clean the float

{% highlight css %}
.cc:after {content: ".";display: block;height:0;clear: both;visibility: hidden;}
.cc {display: inline-block;}
* html .cc {height: 1%;}
.cc {display: block;}
.c{clear:both;font:0px/0px Arial;overflow:hidden;height:0;width:0;}
{% endhighlight %}

##Usage
###1
{% highlight html %}
<!--after the float elements-->
<div class="c"></div>
{% endhighlight %}

###2
{% highlight html %}
<!--if the li is float use cc with ul class to clean float-->
<ul class="cc">
  <li></li>
  <li></li>
  <li></li>
</ul>
{% endhighlight %}
