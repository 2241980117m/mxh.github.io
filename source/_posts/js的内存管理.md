---
title: js的内存管理
date: 2016-08-03 20:48:13
tags:
---
<h2>垃圾回收机制</h2>
js不同于c,c++，拥有对内存的完全掌控，它的内存分配和回收都是自动的。
当一个对象不被其他对象引用时，就会被js里的垃圾回收机制自动清理。
<h2>垃圾回收的两种方法</h2>
<h3>引用计数</h3>
引用计数即当一个对象不被其他对象引用时，内存会被回收。但是它存在循环引用的问题（即两个对象相互引用时会出现内存泄露）
<h3>标记清除</h3>
标记清除就是从全局环境出发，可以到达的对象都是必须存在的，而到达不了的对象是不需要的，它的内存会被回收。（这里不被需要的对象包括了引用计数里提到的不被引用的对象）
