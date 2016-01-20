---
layout: post
title: "struts2执行流程学习分析"
date: 2014-03-05 15:46
comments: true
categories: 
---

####版本说明： [struts2 version: 2.3.8](http://struts.apache.org/release/2.3.x/struts2-core/apidocs/)

* * *

## 部分代码分析

### Struts2部分

#### ActionMapper

* package: org.apache.struts2.dispatcher.mapper

* 类型：是一个接口；

* 作用：http requests和action之间的建立关系，映射；

* 分析：通过传递request，actionName，actionMapping等参数信息，对应可返回ActionMapping，或者从ActionMapping返回请求的uri；



#### ActionMapping

* package:org.apache.struts2.dispatcher.mapper

* 类型：类

* 作用：包含action mapping的信息；

* 分析：含namespace,action的name,对应调用action的method方法，同时维护了一个Map，用于存放请求参数，还有个extension参数，初步推测可能是指定请求的扩展名，如.do,.action，基本情况就是一个java bean充满了get set方法；

* * *

### XWORK部分

#### Action
* package:com.opensymphony.xwork2

* 类型：接口

* 作用：每个Action都需要实现此接口，并暴露execute方法；

* 分析：主要是实现一个execute方法，并带了一些常量；


#### ActionContext
* package:com.opensymphony.xwork2

* 类型：类

* 作用：是一个执行Action的Context（上下文）；

* 分析：每个context类似一个容器，实际上是一个Map，包含了很多action执行时需要的对象，类似session，请求参数，本地化信息，同时，ActionContext是通过thread local实现的，保证当前线程中是唯一的，无需担心Action线程安全问题；

#### ActionInvocation
* package:com.opensymphony.xwork2

* 类型：接口

* 作用：代表了Action执行的状态，拥有拦截器和Action的实例；

* 分析：通过ActionProxy进行初始化，然后连续地调用invoke方法，执行顺序是所有的拦截器，Action，最后是Result。


#### ActionProxy
* package:com.opensymphony.xwork2

* 类型：接口

* 作用：介于XWork和Action之间一个额外的层，同时，可实现不同的Proxy

* 分析：Action的代理，通过内置的一些方法，可得到很多Action相关的信息，得到Action，ActionName，Action配置，执行的一些情况；


#### ActionSupport
* pacage:com.opensymphony.xwork2

* 类型：类

* 作用：提供了普通action的统一实现

* 分析：实现了Action接口，一些验证接口，本地化等方法，详细参见源码；


#### Result
* package:com.opensymphony.xwork2

* 类型：接口

* 作用：Action的执行结果，会映射一个View的实现；

* 分析：Views的方式有swingpanel，另一个action，http重定向，分发另一个http的url

* * *

## 执行流程分析

* 以StrutsPrepareAndExecuteFilter过滤器为例

* package:org.apache.struts2.dispatcher.ng.filter

* 核心方法doFilter

* 首先做一些预处理，编码，本地化，ActionContext等；

* 对请求路径判断处理；

* 如果请求路径符合要求，查找ActionMapping对象，ActionMapping对象是通过ActionMapper的getMapping方法得到的，ActionMapper是通过dispatcher的container中进行注入的，如果返回null，作静态资源处理，否则执行相应的action；

* 最终会清理request;

* 关于详细的执行流程，[参考这里](http://blog.csdn.net/legendj/article/details/9790647)，给出较为详细的执行流行分析，另可参考该文章中执行流程图；

* 个人对于struts2流程的理解图
![struts2-flow](http://pic.yupoo.com/wikimo/DAdGdInU/medium.jpg)