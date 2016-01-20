---
layout: post
title: "Storyboard实例化ViewController时label为null"
date: 2014-02-26 08:50
comments: true
categories: 
---

问题描述：ios下，通过instantiateViewControllerWithIdentifier方法实例化ViewController后，Controller下对应的label为null；

问题分析与解法：原文地址见[http://stackoverflow.com/questions/10780289/how-to-access-properties-of-a-view-controller-loaded-from-storyboard](http://stackoverflow.com/questions/10780289/how-to-access-properties-of-a-view-controller-loaded-from-storyboard)

Your UILabel is nil because you have instantiated your controller but it didn't load its view. The view hierarchy of the controller is loaded the first time you ask for access to its view. So, as @lnafziger suggested (though it should matter for this exact reason) if you switch the two lines it will work. So:

大概意思是，在实例化controller时并未加载view,所以需要添加下view

{% highlight c %}
[self.view addSubview: testController.view];  
testController.label.text = @"newText";
{% endhighlight %}

As an example to illustrate this point, even this one would work:

{% highlight c %}
// Just an example. There is no need to do it like this...
UIView *aView = testController.view;
testController.label.text = @"newText";
[self.view addSubview: testController.view];  
{% endhighlight %}

Or this one:
{% highlight c %}
[testController loadView];
testController.label.text = @"newText";
[self.view addSubview: testController.view];  
{% endhighlight %}

以上提供了3中解法，我选了第1种解法。