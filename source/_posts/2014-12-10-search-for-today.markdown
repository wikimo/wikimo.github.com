---
layout: post
title: "search-model-for-today"
date: 2014-12-10 16:13
comments: true
categories: ruby
---

Sometimes we want to search item for today. For example model is task,To to like it

{% highlight ruby %}
Task.where(created_at: Time.now.midnight..Time.now.end_of_day)
{% endhighlight %}