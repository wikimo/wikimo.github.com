---
layout: post
title: "grape-dev-log"
date: 2015-01-08 10:52
comments: true
categories: ruby grape
---


#### grape remote ip

use env hash 
{% highlight c%}
env['REMOTE_ADDR']
{% endhighlight %}

you can move it to helpers, and include in api
{% highlight c%}
def remote_ip
  env['REMOTE_ADDR']
end
{% endhighlight %}
