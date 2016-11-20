---
title: css中关于margin的问题
date: 2016-10-09 17:27:12
tags:
---
<p>在讲margin的问题时，应该先了解行内元素和块级元素及可置换元素，其中，块级元素(display:block;)是指有确定的宽和高，独立占一行，而行内元素(display:inline;)是指元素能够在一行显示，没有宽度和高度；可置换元素是指占有宽高的行内元素(display:inline-block;)</p>
<hr>
<p>margin对于table及行内元素不起作用，对于行内不可替换元素只有margin-top和margin-bottom不起作用;</p>
<p>对于行内可置换元素padding,margin的各个方向均起作用，对于块级元素也是同样。同时还应该注意垂直外边距的合并问题，即10+15=15;</p>