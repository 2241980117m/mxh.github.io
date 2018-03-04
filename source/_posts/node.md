---
title: node数据库操作及爬虫
date: 2017-08-07 20:23:00
tags:
---

<p>经过为期1-2的周的学习，总算对node有了大致的理解。因为之前了解过PHP，刚开始学习的时候因为node的异步和底层的东西比较多，所以觉得不怎么好用。但是对于大型网站，node的非阻塞确实还是非常提倡的，毕竟不会导致页面停滞下来，可以很好的完成数据交互。</p>
<p>因为这1-2周的学习比较杂乱，node的各个模块都看了些。在这里就不具体的讲述了，只是分享下mysql数据库操作及node爬虫</p>
<h2>学习建议</h2>
<span>在学习node之前，建议大家先了解js的回调函数、异步、npm及HTTP</span>

<h2>数据库操作</h2>
<div>
	  <strong>npm下载mysql模块</strong>
	  <span>npm install mysql</span>
	  <br>
      <div>
		<b>数据库的增删改查</b>
        <span>因为数据库的增删改查只是sql语句不一样，node逻辑相同，因此，只在这里贴出实现数据库查找操作的具体实现.</span>
        <img src="/img/a.png" style="width: 50vw;height: 45vh;">
	    <br>
		<strong>连接池</strong>
		<span>连接池算是node在数据库方面的特色,因为HP是同步的，在这个方面并没有具体的实现。连接池主要是用来一次性创造多个多个连接，当需要使用的时候直接使用，使用完把连接放回去即可。</span>
		<strong>具体实现:</strong>
		<span>创建一个pool.js文件</span>
		<img src="/img/pool.png" style="width: 50vw;height: 58vh;">
		<span>创建pool_node.js文件，引用pool.js实现的接口</span>
		<img src="/img/pool_node.png" style="width: 50vw;height: 20vh;">
		<span>效果展示</span>
		<img src="/img/res1.png" style="width: 50vw;height: 6vh;">
		<br>
		<strong>注意：之前在网上查看下载mysql模块是npm install mysql@版本号,但是在完成数据库查找时发现报错，去掉后面的版本号就好，即npm install mysql.</strong>
	</div>
	<div></div>

</div>
<h2>node实现爬虫</h2>
<strong>建议:了解cheerio、superagent、express框架</strong>
<h3>express实现爬虫</h3>
<span>爬虫https://cnodejs.org/上面的每个话题标题及跳转的链接地址</span>
<span>实现</span><br>
<img src="/img/express.png">
<span style="margin-top: 1vh;">结果</span><br>
<img src="/img/res2-1.png">
<h3>eventproxy</h3>
<span>爬虫https://cnodejs.org/上面的每个话题标题及第一个评论</span>
<span>实现</span><br>
<img src="/img/event-1.png">
<img src="/img/event-2.png">
<h3>async</h3>
<span>爬虫https://cnodejs.org/上面的每个话题标题及第一个评论</span>
<span>实现</span><br>
<img src="/img/async1.png"><br />
<img src="/img/async1.png">
<br>
<span>eventproxy和async实现的爬虫结果截图，仅是一部分</span><br>
<img src="/img/res5-1.png">
<img src="/img/res5-2.png">


<b>eventproxy和async都是流程控制工具，但是async相较于eventproxy，可以控制并发个数，防止请求网站时因为并发量大，而导致IP被封</b>

<h3>上面例子踩过的坑</h3>
1. eventproxy.after('thingname',times,callback(lists))，其中lists为数组，它是经过times次事件名为thingname的事件传递进来的各个参数所形成的数组。
2. async.mapLimit(urlArr,limit,function A(){},function B(){}).其中urlArr为数组，限制并发量为limit,它的每一个元素都要作为A函数的参数进行操作，当A执行完后开始执行B函数，但是A函数中的callback函数的第一个参数只有为null时，才会遍历完整个urlArr.自己对其理解为A函数中的callback函数的参数作为B函数的实参进行调用。

