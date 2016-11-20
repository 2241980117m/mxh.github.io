---
title: XML
date: 2016-08-04 09:14:02
tags:
---
<h2>XML简介</h2>
xml是一种扩展性的标记语言，用来存储和传输数据，没有预定义的标签，允许用户自定义标签，它没有任何作为，而且它是HTML的补充，并不能替换HTML。XML文档是一个纯文本文档，任何可以处理纯文本的软件都可以处理它。
<h2>XML用途</h2>
XML简化数据传输和数据共享，使资源有用。还可以作为一些Internet语言的基础。
<h2>XML文档树</h2>
XML文档包括XML声明和元素，元素之间的关系有父元素，子元素，同胞。所有元素都有内容和属性。XML声明中包含XML文档的版本及编码方式。而元素分为根元素和子元素，根元素是所有子元素的父元素。
<h2>XML语法</h2>
1. 对大小写敏感。
2. 必须要有关闭标签。
3. 属性值要用双引号括起来。
4. 使用实例引用。XML中存在一些特殊符号，必须要用实例代替它。如:<,+,',"". 
5. 与HTML不同，XML会保留空格。
6. XML注释与HTML的注释语法完全相同。
7. XML必须正确嵌套。
8. 使用LF存储换行。
<h2>XML元素</h2>
XML元素指的是开始标签和结束标签之间的内容，包括开始标签和结束标签。XML元素的命名规则有：
1. 名称是字母，数字，其他字符的组合。
2. 名称不能以数字或者标点符号开头。
3. 尽量别再名称里使用-,.和空格。
4. 名称不能以xml,Xml,XML开头
且XML元素是可以扩展的，可以在不中断应用程序进行扩展
<h2>XML属性</h2>
属性提供有关元素的额外信息。如:&lt;img src="#"&gt;中的src属性。
属性不包含在数据部分。
属性值应该用引号括起来，允许单引号包含双引号，或者双引号包含单引号，在属性值中允许使用引用实例。
同时，属性和子元素可以提供相同的信息。
在这里，建议元数据(数据的数据)存储为属性，数据存储为元素，尽可能少的使用属性。
<h2>XML验证</h2>
形式良好的XML文档值的是拥有正确语法的XML文档。
合法的XML指的是通过DTD验证的XML文档，DTD是用来定义XML文档的结构。
可以通过DOCTYPE声明引用DTD文档来验证XML文档。
<h2>XMLHttpRequest</h2>
用来进行后台与服务器的数据交换。
通过它可以进行:
1.在不进行重新加载的情况下进行数据更新
2.可以向服务器发送数据
3.可以从服务器接收数据
4.可以向服务器请求数据
<strong>创建XMLHttpRequest对象</strong>
new XMLHttpRequest();
<h2>XML解析器</h2>
IE解析器可以提供XML文件解析和字符串解析。其他浏览器使用单独的解析器。
下面代码可以将XML文档解析到XML DOM中
&lt;script&gt;
if(window.XMLHttpRequest){
	var xmltxt=new XMLHttpRequest();
}else{
	 xmltxt=new ActiveXObject("Microsoft.XMLHTTP");
}
xmltxt.open("GET",url,false);
xmltxt.send();
var xmltet=xmltxt.responseXML;
&lt;/script&gt;
下面代码可以将xml字符串解析
if(window.DOMParser){
    x=new DOMParser();
    xmltxt=x.parseFromString(xml字符串,text/xml);
}else{
	xmltxt=new ActiveXObject("Microsoft XMLDOM");
	xmltxt.asyne="false";
	xmltxt.loadXML(xml字符串);            //解析xml字符串
}
<strong>这里的parseFromString( )接收2个参数，分别是字符串和内容类型，内容类型始终为text/xml,在发生解析错误时，仍然会返回一个Document类型，文档元素是&lt;parsererror&gt;内容是对解析错误的描述。
且DomParser只能解析格式良好的xml文档，因此他并不能解析html文档.</strong>
<h2>创建空的xml文档</h2>
var xmldom=document.implementation.createDocument(参数1，参数2，参数3);参数具体为:
参数1是指定的命名空间，参数2是xml文档元素的标签,参数3是文档类型。这3个参数都为必选，因此，
尽管你不指定命名空间，也要将其设为空，当不指定文档类型时，将其设为null.
<h2>将HTML文档解析为XML文档</h2>
有两种方法：
<strong>第一种</strong>
首先，应该先创建XMLSerializer的实例，再调用serializeTostring()方法。
<strong>第二种</strong>
DOM中的每个节点都拥有xml属性，它返回指定节点的xml字符串。
<h2>命名空间</h2>
当两个xml文档一起被使用时，如果它们包含相同的元素名，则会发生命名冲突，而xml解析器不会解决这种错误。
解决它有两种方法：1.使用前缀的方法 2.使用命名空间
<strong>前缀</strong>
如:  &lt;table&gt;  可以写成  &lt;h:table&gt;
<strong>使用命名空间</strong>
即给开始标签设置xmlns属性，xmlns的使用方法如下:
xmlns:namespace="###";   这样就为某个前缀设置了与命名空间相关联的限定名称。（它的子元素要加前缀）
带有相同前缀的元素指向同一个命名空间。
<strong>在使用默认命名空间时，可以省略前缀。</strong>
<h2>CDATA</h2>
xml文档中的大部分数据都会被xml解析器解析(包括开始标签和结束标签之间的数据),只有CDATA部分的文本不会被解析。
<strong>将xml作为CDATA的方法</strong>
使用&lt;!--[CDATA[  作为CATAT部分的内容]]&gt;
<strong>CDATA不允许嵌套，CDATA内容部分不允许出现]],结尾的]]&gt;不允许出现空格和换行。</strong>
<h2>注意事项</h2>
xml可以嵌套在html文档中使用（这种用法称为数据岛）,用法是&lt;xml id="" src="##"&gt;id是用来标识xml数据岛，src是指向xml文档。不过这种用法只有IE支持。推荐使用js和xml DOM来解析xml文档。