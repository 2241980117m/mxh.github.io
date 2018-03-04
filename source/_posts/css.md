---
title: css选择符
date: 2018-02-21 20:58:04
tags:
---
<p>之前了解过css class选择器、id选择器、标签选择器。但是之后又了解到了一些其他比较实用的css选择器。自己在这里总结一下。因为对刚刚说过的几个选择器已经很了解了，所以就不再讲述了。</p>
<h2>基本选择器</h2>
<ul>
<li>class选择器</li>
<li>id选择器</li>
<li>标签选择器</li>	
</ul>
<h2>多元素组合的选择器</h2>
<ul>
	<li>多元素选择器  【如：element,element】</li>
	<li>后代元素选择器  【如:element element】</li>
	<li>相邻元素选择器    【如: ele1+ele2,选择的是紧跟在ele1后面的同级子元素】</li>
	<li>子元素选择器     【如: ele1>ele2,作用类似于element element】</li>
</ul>
<h2>属性选择器</h2>
<ul>	
	<li>ele[attr]:匹配所有具有attr属性的ele元素</li>
	<li>ele[attr="*"]:匹配所有attr="*"的ele元素</li>
	<li>ele[attr~="*"]:匹配attr属性等于多个以空格分割的值，其中一个值是*的ele元素</li>
	<li>ele[atrtr|=val]</li>
	<li>ele[attr^=“val”]:匹配含有attr属性，且值以val打头的ele元素</li>
	<li>ele[attr$=“val”]:匹配含有attr属性，且值以val结束的ele元素</li>
	<li>ele[attr*=“val”]:匹配含有attr属性，且值包含“val”字符串的ele元素</li>
</ul>
<h2>伪类选择器</h2>
<ul>
	<li>ele:first-child:匹配ele是第一个子元素的元素。同样，可以使用:nth-child(),接收的参数可以是数字，公式，关键字。类似的，nth-of-type也是如此</li>
	<li>ele:lang(c):匹配lang属性等于c的元素</li>
	<li>ele:not(a):匹配不包含a元素的所有ele元素</li>
</ul>
<h2>伪元素选择器</h2>
<ul>
	<li>ele:before:在ele之前插入生成的内容，内含有content属性</li>
	<li>ele:after:在ele之后插入生成的内容，内含有content属性</li>
	<li>ele:first-line:匹配ele元素的第一行文字</li>
	<li>ele:first-letter:匹配ele元素的第一个文字</li>
</ul>
<h2>同级元素通用选择器</h2>
<ul>
	<li>ele1 ~ ele2:匹配ele1之后的所有同级ele2元素</li>
</ul>

