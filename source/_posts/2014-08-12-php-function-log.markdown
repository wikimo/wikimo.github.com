---
layout: post
title: "php-function-log"
date: 2014-08-12 13:58
comments: true
categories: 
---


###正则表达式


1. 任意字符匹配

{% highlight php%}

#温　度：25~30°风　向匹配结果，将25~30°取出
#(.*)匹配任意字符
 preg_match('/温　度：(.*)风　向/',$weather_str,$match);
var_dump($match);

{% endhighlight %}


2.  大括号，小括号，中括号（方括号）的作用

    * 大括号 重复次数，一般{n,m}重复次数最少n,最多m，{n} 重复n次，{n,}重复n次或更多；
    
    * 小括号，分组
    * 方括号 匹配里面的任意字符；
    

3. 贪婪匹配与懒惰匹配

{% highlight php%}

$str = "21";
#匹配21，贪婪
preg_match('/[123].*/',$str,$match);

#匹配2，懒惰
#preg_match('/[123].*?/',$str,$match);

var_dump($match);


{% highlight php%}
4. 问号
    * 贪婪匹配
    * 匹配问号本身，前面需要加\
    * 出现0次或一次 \(?0\d{2}[) -]?\d{8}，匹配电话号码，像(010)88886666，或022-22334455，或02912345678
    * 不捕捉模式，啥意思 '?:'
    
5. 元字符
    * 点 查找单个字符，除了换行和行结束符
    * \w 匹配字母或数字或下划线或汉字 (大写相反，以下相同)
    * \s 匹配任意的空白符
    * \d 匹配数值
    * \b 匹配单词的开始或结束
    * ^ 匹配字符串的开始 [^x]匹配除了x以外的任意字符
    * $ 匹配字符串的结束    
    
6. 分支条件 
    * 用 “|”分割；    
    

[参考文章](http://deerchao.net/tutorials/regex/regex.htm)

---

###字符串替换
* [str_replace](http://www.w3school.com.cn/php/func_string_str_replace.asp) //字符串替换
* [stripos](http://www.w3school.com.cn/php/func_string_stripos.asp) //查找字符串位置
* [ucfirst](http://www.w3school.com.cn/php/func_string_ucfirst.asp) //首单词字母大写
* [ucwords](http://www.w3school.com.cn/php/func_string_ucwords.asp) //单词首字母大写
* [wordwrap](http://www.w3school.com.cn/php/func_string_wordwrap.asp) //指定换行

---

###字符数组转换
* [explode](http://www.w3school.com.cn/php/func_string_explode.asp)(separator,string,limit) #字符串分割成数组；
* [implode](http://www.w3school.com.cn/php/func_string_implode.asp)(separator,array) #数组合并为字符串；

---

###数组分割并赋值

{% endhighlight %}
##分割字符串并复制给变量$a,$b,$c
$my_array = array("Dog","Cat","Horse");

list($a, $b, $c) = $my_array;
{% endhighlight %}

---

### 特定字符前加斜杠
* [addcslashes](http://www.w3school.com.cn/php/func_string_addcslashes.asp)
* [stripcslashes](http://www.w3school.com.cn/php/func_string_stripcslashes.asp)


---

### HTML与字符转换
* [html_entity_decode](http://www.w3school.com.cn/php/func_string_html_entity_decode.asp) 把 HTML 实体转换为字符
* [htmlentities](http://www.w3school.com.cn/php/func_string_htmlentities.asp) 把字符转换为 HTML 实体
* [htmlspecialchars_decode](http://www.w3school.com.cn/php/ func_string_htmlspecialchars_decode.asp) 把一些预定义的 HTML 实体转换为字符
* [htmlspecialchars](http://www.w3school.com.cn/php/func_string_htmlspecialchars.asp) 把一些预定义的字符转换为 HTML 实体
* [nl2br](http://www.w3school.com.cn/php/func_string_nl2br.asp) 换行符->br
* [strip_tags](http://www.w3school.com.cn/php/func_string_strip_tags.asp) 去除 HTML、XML 以及 PHP 标签

---

### 其它常用函数参考(来源：w3school)
* [Array](http://www.w3school.com.cn/php/php_ref_array.asp)
* [Date](http://www.w3school.com.cn/php/php_ref_date.asp)
* [Directory](http://www.w3school.com.cn/php/php_ref_directory.asp)
* [String](http://www.w3school.com.cn/php/php_ref_string.asp)