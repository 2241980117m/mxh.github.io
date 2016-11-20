---
title: php内置处理函数
date: 2016-09-21 21:58:53
tags:
---
在这里，总结一下近期自己学过的一些php处理函数，按照处理函数处理的对象的不同来逐个说明。
<hr />
<h2>变量</h2>
<strong>gettype()</strong>
<p>参数是变量名，用来获取变量的类型。</p>
<strong>settype()</strong>
<p>参数是变量名及要设置的变量的数据类型。类型应该是单引号的字符串形式。</p>
<strong>isset()函数</strong>
<p>参数是变量名,检查变量是否存在，存在返回true.</p>
<p>这里的参数可以是一个变量或者是一个以逗号分隔的变量列表!</p>
<strong>unset()</strong>
<p>参数是变量名，用来销毁一个变量.</p>
<strong>empty()</strong>
<p>参数是变量名，检测一个变量是否存在，并且这个变量的值是否为0或空值，若是则返回true.</p>
<strong>intval(),floatval(),strval()</strong>
<p>可以根据函数名前面的名称判断将一个变量转化后的数据类型。其中将一个字符串传入intval()中，可以同时传递一个将此变量转化为整数的进制数。</p>
<h2>文件处理函数</h2>
<strong>fopen()</strong>
<p>用来打开文件，参数有2个，分别是文件指针文件模式，第两个参数必须是字符串形式,成功时返回一个文件指针</p>
<strong>fwrite()</strong>
<p>该函数用来写文件，它有3个参数，分别是文件指针，字符串变量或者字符串，字符串长度。</p>
<strong>fclose()</strong>
<p>用来关闭文件，参数是文件指针。关闭成功时返回true.</p>
<strong>feof()不再介绍</strong>
<strong>fgets()</strong>
<p>有两个参数，分别是文件指针和字符串长度，每次读取一行内容，遇到\n或者EOF或者达到最大长度时结束。可以读取到的最大长度是指定长度-1.</p>
