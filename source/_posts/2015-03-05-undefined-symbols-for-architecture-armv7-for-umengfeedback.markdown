---
layout: post
title: "undefined symbols for architecture armv7-for-umengfeedback"
date: 2015-03-05 09:27
comments: true
categories: ios
---

问题描述： 在使用友盟用户反馈的时候，遇到这样的错误“undefined symbols for architecture armv7”，提示 [UMRecorder recorder] in libUMFeedback.a

解法：加入语音模块framework即可；