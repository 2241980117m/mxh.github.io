---
title: css3属性深入
date: 2018-02-20 18:53:51
tags:
---
<p>近段时间在看&lt;&lt;css揭秘&gt;&gt;这本书，它注重代码的简洁和可重用性。这本书适合css进阶的时候看，在看这本书时，建议了解一下css、scss。个人还是觉得这本书是不错的。</p>
<p>
	自己现在只看了前四章，在这里简洁的总结下自己对一些属性的新的理解。
</p>
<div>
<h3>之前没有了解过的</h3>
<ul>
	<li>currentColor</li>
	<li>calc()函数</li>
</ul>
<h3>背景</h3>
<ul>
<li>background-clip:裁剪背景;可以设置为border-box、padding-box、content-box;</li>
<li>background-attachment:设置背景的位置，可以取值为scroll、fixed;</li>
<li>background-position:支持right 20px top 10px;这样的值</li>
<li>background-origin:设置背景起点。取值和background-clip相同;</li>
<li></li>
</ul>
</div>
<div>
<h3>多重边框</h3>
<p>ps:自己之前实现多重边框时都是用父子div来实现的，但是了解到其它的方法，不得不说真的很方便</p>
<ul>
	<li>box-shadow:这个属性是用来产生投影的，不会影响布局。参数分别是:水平投影长度，垂直投影长度，模糊距离，扩张半径，向内扩张或者向外扩张（默认向外）。当模糊距离小于或等于负的扩张半径时，投影我们是看不到的。box-shadow可以设置多个值来达到多重边框的效果，但是要注意它会覆盖之前的值，也就是说我们在想要达到两重边框时，需要设置第二个值的扩张半径大于第一个值的扩张半径。</li>
	<li>outline:取值和border相同，只能设置一个值。</li>    
</ul>
 <p>ps:outline、box-shadow的区别是outline不一定紧贴border-radius,而box-shadow紧贴</p>
</div>
<div>
<h3></h3>
 
</div>
<div>
<h3>css渐变</h3>
  <ul>
  	<li>linear-gradient(线性渐变):参数分别是角度（deg,to bottom right）、起始颜色、起始位置、结束颜色、结束位置。当结束位置为0时，取前面位置的最大值。</li>
  	<li>radial-gradient(垂直渐变)：</li>
  	<li>repeating-linear-gradient:</li>
  	<li>repeating-radial-gradient:</li>
  </ul>
</div>
<hr/>
