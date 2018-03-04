---
title: Ajax
date: 2016-08-10 14:36:55
tags:
---
<h2>简介</h2>
AJAX（异步的JavaScript和XML）不是一种语言，而是一种使用现有标准的新方法，在不更新页面的情况下，实现和服务器交换数据并动态更新网页。它的核心是XHR对象。
<h2>XHR对象</h2>
<b>创建XHR对象</b>
      var xhr=new XMLHttpRequest();
      XHR对象拥有2个方法，4个属性。以下将分别讲解。
<b>方法</b>
- open()
它接收3个参数,分别是请求方法，请求URL，是否异步处理。但是open()并不是真正发送请求，仅是启动一个请求以备发送。
- send()
它接收参数，即作为主体要发送的数据，没有要发送的数据时，为避免出错参数为null.
<strong>属性</strong>
- responseText
被返回的文本，无论返回的内容类型是什么，返回的文本都会存在这里。
- responseXML
当返回的文本内容类型为XML时，返回的文本将会保存在这里。
- status
响应的HTTP状态（HTTP状态代码为200时，表示响应成功;HTTP状态代码为304时，表示请求的资源没有改变。）
- statusText
HTTP状态说明
<strong>是否异步处理</strong>
当open()的第三个参数为false时，表示同步处理（js代码会等到服务器响应之后再继续执行），
收到响应后，响应内容被保存在XHR的属性中。
当open()的第三个参数为true时，表示异步处理（js代码继续执行，不用等待响应），此时应该检测readyState属性。
readyState的值和代表含义如下 :
0 ------ 没有调用open();
1 ------ 调用open(),没有调用send();
2 ------ 调用send(),没有收到响
3 ------ 已经接收到部分响应数据
4 ------ 已经接收到全部的响应数据
当readyState的值改变时，会触发onreadystatechange事件。不过在调用open()之前指定onreadystatechange事件处理程序才能保证跨浏览器兼容性。
<strong>取消异步处理</strong>
可以通过调用abort()实现。
<h2>HTTP头部信息</h2>
<strong>setRequestHeader()</strong>
可以设置自定义的请求头部信息，接收两个参数,分别是：头部字段的名称，头部字段的值。在open()之后，send()之前调用它
<strong>getResponseHeader()</strong>
接收一个参数，即头部字段的名称，返回对应的头部字段的值。
<strong>getAllResponseHeaders()</strong>
返回包含所有头部信息的长字符串。
<h2>请求方法</h2>
<strong>GET</strong>
用于从服务器查询信息。可以将查询字符串置于URL的末尾。查询字符串每个参数的名称和值都必须是encodeURIComponent()进行编码。
<strong>POST</strong>
用于向服务器发送应该被保存的信息，post请求的主体可以包含非常多的数据，格式不限。post请求的第二步就是send()，send()的参数必须是xml文档,文档经序列化以后作为请求主体被提交到服务器。
但是,服务器对post请求和web表单请求不会一视同仁，我们就需要程序读取发送过来的数据，提取出有用的部分，可以用XHR模仿表单提交，将Content-Type的头部信息设为application/x-www-form-urlencoded,将表单信息序列化，再通过XHR发送到服务器。
<h2>FormData类型</h2>
FormData类型为序列化表单和创建于表单数据格式相同的数据提供了便利。
<strong>创建FormData对象</strong>
    var form=new FormData();
    form.append("name","a");
append()函数接收两个参数，分别是；对应表单字段的名字和字段中包含的值。
也可以向FormData()构造函数中传入表单元素。
<h2>超时设定</h2>
仅IE8支持，IE8改XHR对象添加了timeout属性，给timeout属性设置一个值,当响应时间超过这个值时，就会执行ontimeout事件
<h2>overrideMIMEType()</h2>
返回响应的MIME类型决定了XHR对象如何处理返回的文本，当MIME为text/plain,但实际上数据是XML，则responseText属性中是null.通过调用overrideMIMEType()可以设置MIME类型。参数是MIME类型
<h2>进度事件</h2>
一共有6个进度事件，只在这里讲述其中2个事件。
- load事件
当响应接收完毕后会触发load事件，用以替代onreadystatechange事件，而onload事件处理程序会接收到event对象，它的target属性会指向XHR对象实例，访问到它的所有属性和方法。
- progress事件
会在浏览器接收新数据期间周期性的触发，progress事件处理程序会接收event参数,它的target属性指向XHR对象，不过他还有3个额外的属性,分别是:lengthComputable(表示进度信息是否可用),totalSize(预期的字节数),position(已经接收到的字节数).
<h2>跨源资源共享</h2>
<b>什么是跨域</b>
   <p>请求的url的协议，域名，端口三者任一与当前页面不同即为跨域。</p>
<strong>XDR</strong>
IE8引入了XDR，与XHR类似，但能实现跨域通信，而XHR只能访问与他的页面位于同一域的资源。且cookie不随请求发送，不随响应返回，不能访问响应头部的信息，
只能修改请求头部的Content-Type字段,只支持get和post请求.且所有的XDR请求都是异步执行的。
<strong>XDR对象的使用方法</strong>
var xdr=new XDomainRequest();
xdr.onload=function(){
	alert(xdr.responseText);
}
xdr.open("get","####");
xdr.send(null);
<strong>同样,XDR对象也支持timeout属性以及timeout事件处理程序</strong>
为支持post请求,XDR对象也支持ContentType属性,用来表示发送数据的格式。
而其他浏览器只需要将open()中的第二个参数url设为绝对URL即可。跨域XHR同时存在一些限制（为了安全考虑），如；
1.不能使用setRequestHeader()设置自定义头部。
2.不能发送和调用cookie.
3.使用getAllRequestHeaders()返回空字符串。
<strong>动态创建script标签</strong>
  img标签的src可以实现跨域，script的src也可以实现跨域。如:
    var script=document.createElement("script");
    script.src="  "; //填写请求的url
    document.body.appendChild(script);
<strong>带凭据的请求</strong>
一般地，跨域请求不提供凭据(cookie,客户端SSL证明,HTTP认证)，但是通过withCredentials属性设为true,可以指定某个请求发送凭据。如果服务器接收这个请求就会用下面的HTTP头部来响应；Access-Control-Allow-Credentials:true.如果服务器的响应里没有包含这个头部，则浏览器不会把响应交给JS，responseText的值是空字符串。
<strong>Jquery Ajax</strong>
通过Jquery Ajax的JSONP实现跨域请求。
   






