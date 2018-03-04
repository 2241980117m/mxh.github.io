---
title: CSS的float,BFC
date: 2017-05-12 20:40:17
tags:
---
<p>今天在写网页的时候突然发现给父元素设置text-align:center;子浮动元素不会脱离文档流,百思不得其解。重新看了下关于float的相关知识，就在这里和大家分享一下。</p>

<h2>float</h2>
- 设置float的元素最后都会生成块级框。即不管设置float的元素是块级元素、行内元素，最后都可以设置width,height属性。
- 设置float的元素没有设置width,height属性的话，则该元素会尽可能小的显示。
- 设置float的元素会脱离文档流,但是却不会脱离文档流。即其他的布局元素会忽视float元素进行布局，但是文字会认为float元素存在，围绕float元素进行布局。
- 设置float元素会默认显示在父元素的paddding之内。
- float元素会脱离文档流,但是当float元素的父元素也设置了float属性，则子元素会包含在父元素里。这就是float的延展性。
<h2>clear属性</h2>
clear属性可以取left,right,both值。但是在这里需要注意地点，设置clear的元素只会对其自身的布局有影响。
<h2>清除浮动</h2>
<p>清除浮动有2种方法，分别是:</p>
- 给父元素设置overflow:hidden;
- 给最后一个设置float的元素的后面添加一个设置clear:both的元素
<h2>BFC</h2>
<p>BFC就是块级格式化上下文。生成BFC的情况有以下几种:</p>
- 设置float的元素
- position的值为absolute、fixed的元素
- 非块级盒子的块级容器
- overflow值不为visiable的元素
- 这里推荐一个教程，以便大家更好的了解及应用BFC <a href="https://www.w3cplus.com/css/understanding-bfc-and-margin-collapse.html">BFC深入理解</a>
<hr>
<h2>具体看的资料</h2>
<a href="http://www.cnblogs.com/starof/p/4608962.html">深入理解CSS浮动</a>
<a href="http://luopq.com/2015/11/08/CSS-float/">详解CSS float</a>