---
layout: post
title: "关于phpwind上传简要分析(flash upload)"
date: 2012-10-30 11:34
comments: true
categories: 
---

version:8.7
涉及的文件主要包括：
1)job.php
2)pw_ajax.php
3)ctions/ajax/,actions/job下

如果自己额外扩展文件，都需要在job.php,pw_ajax.php文件中指定白名单。

文件上传以actions/job/mutiupload.php为例，最终调用了
{% codeblock lang:php%}
PwUpload::upload($mutiupload);
{% endcodeblock %}
方法进行上传，最后输出json数据，json数据格式为aid,path,aid为附件图片id,path为图片路径，供前台展现用；

文件删除以actions/ajax/delmutiattone.php，删除帖子图片为例，最终调用
{% codeblock lang:php%}
pwDelThreadAtt($rt['attachurl'], $db_ifftp, $rt['ifthumb']);
$db->update("DELETE FROM pw_attachs WHERE aid=" . S::sqlEscape($aid) . " LIMIT 1");
{% endcodeblock %}
删除实际图片文件以及数据库记录

