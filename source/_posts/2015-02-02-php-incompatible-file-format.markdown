---
layout: post
title: "php-incompatible-file-format"
date: 2015-02-02 15:01
comments: true
categories: php
---


* issue: 'Fatal error: Incompatible file format: The encoded file has format major ID 3, whereas the Loader expects 4 in'

* 原因：php文件被Zend加密打包过，当前php运行环境没有很好地支持；

* 解法：
   1. 可以把PHP程序源文件在Zend Guard下重新加密;

   2. 也可以把程序放到PHP5.2 + Zend Optimizer的环境下运行即可;


* 环境参考：
  1. PHP5.3.17 + Zend Engine v2.3.0 + Zend Guard Loader v3.3
  2. PHP5.2.17 + Zend Engine v2.2.0 + Zend Optimizer v3.3.9
  3. PHP5.2.14 + Zend Optimizer v3.3.3 （我的问题解法）

* 参考资源：
  1. [http://blog.is36.com/zend_php_incompatible_file_format/](http://blog.is36.com/zend_php_incompatible_file_format/)
  2. [http://blog.saymoon.com/2012/09/linuxnginx_multi_version_php/](http://blog.saymoon.com/2012/09/linuxnginx_multi_version_php/)