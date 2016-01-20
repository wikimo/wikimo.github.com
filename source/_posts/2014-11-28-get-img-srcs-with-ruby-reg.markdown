---
layout: post
title: "get-img-srcs-with-ruby-reg"
date: 2014-11-28 12:45
comments: true
categories: ruby
---

description: want to get the html img src with an array in ruby

{% highlight ruby%}
html = <<EOF
    <div>
        <img alt='test' src="/UpLoad/image/111.jpg" /><img alt='test2' src='/UpLoad/image/222.jpg' /><img
            src='./UpLoad/image/222.jpg' alt='' /></div>
    <div>
        <img alt='' src='/UpLoad/image/333.jpg' />
        <img src='../test/UpLoad/image/444.jpg' alt='test3' />
    </div>

EOF

imgs = html.scan(/<img[^>]+src\s*=\s*['\"]([^'\"]+)['\"][^>]*>/).flatten 

p imgs

{% endhighlight %}
