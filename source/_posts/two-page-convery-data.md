---
title: 'web实现的数据在两个页面之间传递'
date: 2017-06-02 22:17:49
tags:
---
<p>在平时练习中我们经常会用到数据在两个页面之间传递，比如博客登陆成功后，需要拥有权限去写博客，而为了防止大家直接跳到某个页面执行相同的操作，我们需要在登陆成功后做一个标记，而第二个页面有这个标记时，才会赋予用户权限。</p>
<p>常见的数据在两个页面中传递的方式有以下几种:</p>
<ul>
	<li>
		<h2>session</h2>
		<p>牵扯到后台，要用session来做的话，注意如果跨域的话，需要设置withCredentials:true.</p>
	</li>
	<li>
		<h2>window对象</h2>
		<p>window代表的是打开的窗口或者frame，当两个页面在同一个窗口中展示的话，可以通过window对象来传递数据</p>
	</li>
	<li>
		<h2>cookie</h2>
		<p>可以在第一个页面设置cookie，在第二个人页面通过字符串方法筛选出传递的值</p>
	</li>
	<li>
		<h2>url</h2>
		<p>通过url后面的查询字符串来筛选出</p>
	</li>
	<li>
		<h2>隐藏的表单域</h2>
		<p>通过form表单进行提交,指定action为第二个页面的地址</p>
	</li>
	<li>
		<h2>本地存储</h2>
		<p>比如：localStorage</p>
	</li>
	<li>
		<h2>windows.postMessage</h2>
		<p>特点是可以进行跨域传输。传输的数据可以是字符串或者是对象，但是有的浏览器不支持对象传递</p>
	</li>
	
</ul>
