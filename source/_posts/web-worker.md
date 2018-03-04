---
title: web worker
date: 2017-12-09 13:00:53
tags:
---
<p>web worker则实现了js的多线程。web worker的执行不影响主线程的执行，同时主线程的执行不会影响到web worker线程的执行。当主线程需要进行大量的异步操作或者是大量的计算时，可以考虑使用web worker.</p>
<h2>原理</h2>
<p>主线程通过web worker在后台执行一系列计算或者异步操作，使得主进程能够不发生阻塞情况，带给用户良好的用户体验。</p>
<h2>web worker子线程的局限性</h2>
<ul>
	<li>同域限制</li>
	<li>DOM限制。子线程不支持全局变量，如:window，document等，但是支持navigator</li>
	<li>脚本限制。子线程不支持全局方法。比如:alert,confirm</li>
	<li>文件限制。子线程不支持读取本地文件</li>
</ul>
<h2>分类</h2>
<ul>
	<li>
		<h3>只与父进程进行通信的普通worker</h3>
	</li>
	<li>
		<h3>shared worker</h3>
	    <p>可以在多个浏览器下实现数据共享</p>
	</li>
	<li>
		<h3>service worker</h3>
    <p>前两种都只可以在网页中运行，当网页关闭worker线程关闭。而service worker可以不依赖网页运行。他提供cache API和拦截请求。cache仅在数据删除时，缓存会删除，使用cache API会忽略报文头中的指定是否过期的HTTP信息头。</p>
	</li>
</ul>