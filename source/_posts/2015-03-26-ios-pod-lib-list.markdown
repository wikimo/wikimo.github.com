---
layout: post
title: "ios-pod-lib-list"
date: 2015-03-26 09:51
comments: true
categories: ios
---


CocoaPods是一个很好的ios 第三方库依赖管理工具，如果你使用过Ruby / Ruby on Rails 那就一定不陌生了，通过一个配置文件中列举第三方库包名，版面，然后通过命令行自动安装，非常方便。

关于CocoaPods的使用，可以参考 [用CocoaPods做iOS程序的依赖管理](http://blog.devtang.com/blog/2014/05/25/use-cocoapod-to-manage-ios-lib-dependency/)

以下列举了我在项目（项目还在审核中）过程中使用到的一些第三方库

* AFNetworking 非常著名，通过网络进行各种http操作时使用，如通过api获取json数据 [https://github.com/AFNetworking/AFNetworking](https://github.com/AFNetworking/AFNetworking)

* Masonry 由于现在ios设备尺寸的问题，需要适应各种尺寸的设备，但官方提供的api又比较繁琐不好使，于是就出现了这个工具，顿时爽了； [https://github.com/Masonry/Masonry](https://github.com/Masonry/Masonry) 

* MJRefresh 常用于tableview数据刷新工具，很好使，作者还有ios培训视频可以看看，感觉讲的还可以的； [https://github.com/CoderMJLee/MJRefresh](https://github.com/CoderMJLee/MJRefresh) 

* UIImage-ResizeMagick 用于修改图片大小 [https://github.com/mustangostang/UIImage-ResizeMagick](https://github.com/mustangostang/UIImage-ResizeMagick)

* GRMustache hybird时可能会用到的模板库，即navtive app + h5 app时，通过objc 设置模板变量的方式，支持一些简单的逻辑判断，循环，但对我来说够用了 [https://github.com/groue/GRMustache](https://github.com/groue/GRMustache)

* WebViewJavascriptBridge hybird时，objc / js 交互时使用，objc / js 可以相互发消息，即发指令，调用对方的方法 [https://github.com/marcuswestin/WebViewJavascriptBridge](https://github.com/marcuswestin/WebViewJavascriptBridge)

* MBProgressHUD 各种提示框，进度条的展示，可灵活自定义 [https://github.com/jdg/MBProgressHUD](https://github.com/jdg/MBProgressHUD) 

* SWRevealViewController 侧划菜单 [https://github.com/John-Lluch/SWRevealViewController](https://github.com/John-Lluch/SWRevealViewController)

* ADDropDownMenuView select / dropdown 下拉选择，如果你有更好的，请麻烦告诉我下，谢谢！ [https://github.com/Antondomashnev/ADDropDownMenuView](https://github.com/Antondomashnev/ADDropDownMenuView)

* EAIntroView app启动时应用介绍页，各种定制，非常好使 [https://github.com/ealeksandrov/EAIntroView](https://github.com/ealeksandrov/EAIntroView)

* UMengSocial / UMengAnalytics 就不介绍了，友盟的社会化组件及统计分析工具

* 最后再介绍一个比较好使的数据筛选下拉库，没有pod，需要自己手动加载，之前使用过程中发现了bug，提交了pull request，发现作者没合并，不过修复了，在行数计算的时候因为数据类型关系，行数会有误差 [https://github.com/jsfu/JSDropDownMenu](https://github.com/jsfu/JSDropDownMenu)