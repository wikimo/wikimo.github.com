---
layout: post
title: "ruby-dev-log"
date: 2014-11-06 16:56
comments: true
categories: 
---


### [collect_with_index](http://apidock.com/ruby/Array/collect#872-collect-with-index)

{% highlight ruby %}
require 'enumerator'

['a', 'b', 'c'].enum_for(:each_with_index).collect do |item, index| 
  "#{index}: #{item}" 
end
{% endhighlight %}

### [permit-array-rails-strong-parameters](http://jaketrent.com/post/permit-array-rails-strong-parameters/)

* which version happened rails 4+

* why: The most standard use case for permit is to pass it a collection of :symbols. These keys must represent scalar values (string, number, that sort) only.

* how to solve

{% highlight ruby %}
params[:luchador][:wins] ||= []
params.require(:luchador).permit(:favorite_move, :weight, wins: [])
{% endhighlight %}
