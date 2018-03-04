---
title: ES6 String extension
date: 2017-05-22 20:14:31
tags:
---
<p>今天看了一下关于ES6的字符串扩展，才对字符串有了进一步的认识。下面就总结下自己的收获。</p>
<h2>字符的表示方法</h2>
<p>以下几种方式可以表示字符'z'</p>
- \z
- \x7A
- \172
- \u007A
- \u{7A}

<hr />

<p>在这里，我先说一下JS的字符都是2个字节的。Unicode编码超过\uFFFF的话，用以下的函数会出现不被预料的错误。</p>


<h2>JS支持的字符函数</h2>
  - charAt():根据下标返回对应的字符
  - charCodeAt():根据下标返回对应字符的Unicode编码
  - fromCharCode():根据Unicode编码返回对应的字符
  - for循环:实现对字符串的遍历
  - indexOf():返回值是boolean值，用来实现一个字符串里是否包含子字符串。

<p>如果字符的Unicode编码超过\uffff的话，可以使用以下函数：</p>
<h2>ES6支持的字符函数</h2>
- codePointAt:返回指定下标字符Unicode编码
- fromCodePoint():根据Unicode编码返回对应的字符
- for of : 实现字符串的遍历
- startsWith(str,index): 用来实现从index下标起，字符串以str子字符串开头
- includes(str,index): 用来实现从index下标起，字符串是否包含str子字符串
- endswith(str,index): 用来实现从开始到index下标之间，字符串以str子字符串结束
- repeat(num): 返回num个重复的字符串，向下取整。num为0到-1的话，取值为0
- padStart(length,str): 用str开头来填补字符串，直到字符串的长度为length
- padEnd(length,str): 用str作为结束来填补字符串，直到字符串的长度为length

<h2>模板字符串</h2>
  将字符和变量、对象、函数全部封装在 ``中，实现模板字符串
