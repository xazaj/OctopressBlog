--- 
categories: 
  - JavaScript
comments: true
layout: post
published: true
status: publish
tags: 
  - indexOf
  - java
  - JavaScript
  - stringObject.查找
title: "JavaScript indexOf() 方法"
type: post
---
定义和用法

indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置。
语法

stringObject.indexOf(searchvalue,fromindex)

参数 	描述
searchvalue 	必需。规定需检索的字符串值。
fromindex 	可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的首字符开始检索。
说明

该方法将从头到尾地检索字符串 stringObject，看它是否含有子串 searchvalue。开始检索的位置在字符串的 fromindex 处或字符串的开头（没有指定 fromindex 时）。如果找到一个 searchvalue，则返回 searchvalue 的第一次出现的位置。stringObject 中的字符位置是从 0 开始的。
提示和注释

注释：indexOf() 方法对大小写敏感！

注释：如果要检索的字符串值没有出现，则该方法返回 -1。
实例

在本例中，我们将在 "Hello world!" 字符串内进行不同的检索：

<script type="text/javascript">// <![CDATA[


var str="Hello world!"
document.write(str.indexOf("Hello") + "
")
document.write(str.indexOf("World") + "
")
document.write(str.indexOf("world"))

// 

以上代码的输出：

0
-1
6]]></script>
