---
title: 如何获取html元素的css样式
date: 2016-07-22 16:04:16
tags:
---
<h2>获取html节点的方式</h2>
  - document.getElementById("#") &nbsp;&nbsp;&nbsp;&nbsp;    //获取id为#的节点
  - document.getElementsByTagName("#") &nbsp;&nbsp;&nbsp;&nbsp; //获取html标签为#的所有节点
  - document.getElementsByClassName("#") &nbsp;&nbsp;&nbsp;&nbsp; //获取类名为#的所有节点
  - 如果获取的是所有节点，可以通过偏移量获得具体的节点
  如：var a=document.getElementsByTagName("#")[0];
   //获取第一个标签名为#的节点
<h2>获取html元素的css样式的方法</h2>
<h2>element.style</h2>
 通过上述方法可以获取到html节点，可以用节点名的style修改css样式，如果是使用的是外联样式表，
   则会在内嵌样式上显示操作的样式。
   如: (接上面的例子)
   a.style.color="red";
   这样a的文字颜色就会变成red.
<h2>getcomputedStyle()</h2>
   - 注意：这种方式只能读，不能写。即不能改变元素的css样式
    document.defaultView.getComputedStyle()
    接收2个元素，分别是：计算元素的样式，伪元素字符串。若不需要伪元素字符串，第二个参数是null.