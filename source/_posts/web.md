---
title: 实现web存储的几种方式
date: 2017-06-02 22:18:38
tags:
---
<h2>Storage类型</h2>
<p>	Storage类型提供了以下几种方法:</p>
- setItem():设置键值对
- getItem():读取指定的元素
- clear():清除所有值
- removeItem():删除指定的元素

其中,Storage类型的值可以通过.或者[]访问到。
<h2>localStorage</h2>
<p>localStorage不会指定任何的访问规则，因为他已经指定好了。在相同的域名(子域名无效)、端口、协议下访问。相当于globalStorage[location.host].它和sessionStorage相同，只保存特定于某个会话的内容。生命周期是截止到调用clear方法，否则一直存在</p>
<h2>globalStorage</h2>
<p>可以实现跨越会话存储数据。需要指定哪些域可以访问该数据，可以通过方括号标记使用属性来实现.共享的数据限制在相同域名，端口，协议下使用，且它保存的数据存储在磁盘里</p>
<h2>sessionStorage</h2>
<p>只适合于存储特定会话内容。即只允许在生成它的页面访问，对多页面应用有限制。</p>
<h2>Cookie</h2>
<p>可以通过document.cookie=decodeURIComponent("name")+decodeURIComponent("value")来设置。在读取的时候使用decodeURIComponent来解码。在必要时需要设置Domain,path,secure值。cookie不安全，且浏览器会对cookie的数目和长度进行限制。但是子cookie会适当解决cookie数量的限制问题。并且在相同的协议，主机，端口下，cookie会被默认发送，从而影响网站的性能</p>