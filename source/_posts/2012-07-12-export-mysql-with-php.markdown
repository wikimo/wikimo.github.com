---
layout: post
title: "在phpmyadmin失败的情况下，用php导出mysql部分数据"
date: 2012-07-12 17:12
comments: true
categories: 
---

要导出mysql的部分数据，有时基本可以用phpmyadmin搞定，但是有时候用phpmyadmin导出的时候会出现语法错误之类的。google稍微搜了下，也没有好的解决方案，那就自己写代码搞定。在此我只是做了一个简单的例子，通过获取数据表的字段，然后拼接字符串输出所需的sql，当然这里没有存成相关的sql文件，只是浏览器输出下，之后可以存成sql文件，最后一个地方不太完美，逗号需要改成分号，这里只是提供一种思路，有空的时候再完善下，可以直接导出文件比较好。

{% highlight php%}
<?php
$db_host = "localhost";
$db_name = "test";
$db_user = "root";
$db_pass = "wiki";
$db_charset = "gbk";
$table_name =  'pw_posts';

$connection = mysql_connect($db_host,$db_user,$db_pass);

mysql_select_db($db_name,$connection);

mysql_query("set neams $db_charset");

$sql = "select * from $table_name  limit 1";

$result = mysql_query($sql);

//get the count of fields
$field_count = mysql_num_fields($result);

$fields = array();

for($i=0;$i < $field_count;$i++){
	//get table columes of field
	array_push($fields,mysql_field_name($result,$i)); 
 
}

//select the data which you want
$sql = 	"SELECT * FROM $table_name  where tid in (SELECT tid FROM pw_threads where authorid=28491)";

$query =  mysql_query($sql);
$insert_sql = "insert into $table_name  (".implode(',',$fields).") values <br/>";
while($record = mysql_fetch_array($query)){
	$item = "(";
	foreach ($fields as $value) {
		if(is_numeric($record[$value])){
			$item .= $record[$value].',';
		}else{
			$item .= "'".$record[$value]."',";
		}
		
	}
	$item =  rtrim($item,',').'),<br/>';
	$insert_sql .= $item;
}
echo $insert_sql;
mysql_close($connection);

?>
{% endhighlight %}