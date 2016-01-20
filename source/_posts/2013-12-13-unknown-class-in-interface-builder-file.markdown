---
layout: post
title: "Unknown class  in Interface Builder file"
date: 2013-12-13 13:39
comments: true
categories: 
---

编译运行的时候提示找不到类，解法在[这里](http://stackoverflow.com/questions/1725881/unknown-class-myclass-in-interface-builder-file-error-at-runtime) 第15


Go to the "ProjectName" , click on it , and then go the "Build phases" tab , and then click on the "compile sources" , and then click on "+" button , a window will appear , the choose "MyClass.m" file and then click "add" ,

Build the Project and Run it , the problem will surely get solved out
