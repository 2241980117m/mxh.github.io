---
title: JS的引用类型及其方法
date: 2016-07-20 17:14:05
tags:
---
<h1>引用类型</h1>
<h2>概念</h2>
引用类型指的是由多个变量组成的对象。javascript不允许访问对象的内存空间。
 当复制引用类型值的时候将变量的地址复制给新的变量，它们指向的是堆中的相同空间。
 <hr />
 <h2>常见的引用类型</h2>
  **Object类型**
   1. 定义
    定两种义有2种方法：1.new + object 构造函数 2.对象字面量的方法
    - new + object 构造函数
    如：	    
	    `var myobject=new object();`
	    `myobject.age=10;`
	    `myobject.name="john";`
    - 对象字面量的方法
	   var myobject={
	      name:"john";															
	      age:10;
	     };	    
	以上两种方法建立的myobject相同。
	2. 访问object的属性
	  	- 点表示法
	       `alert(myobject.name);`    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//john
	  	- 使用方括号
	       `alert(myobject["name"]);`      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//john
	       
<strong>Array类型</strong>
   1.定义
    定义有2种方法：
      1.构造函数   2.数组字面量表示法
- 构造函数
      		`var myArray=new Array();`
      		其中，可以向构造函数里面传递数组长度，也可以传递数组元素。
- 数组字面量表示法
      		var myArray=[]   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//创建一个空数组
      		可以向[]里面放入数组元素，不过数组元素需要字符串表示.每个数组都有length属性
    2.检测数组
        通过Array.isArray()方法检测数组    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//确定是不是数组
    3.方法
- 转换方法
         1.每个对象都有tostring(),tolocalstring(),valueof()方法。
           tostring():&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;返回以逗号分隔的数组元素的字符串表示，
           valueof()和tolocalstring()与它相同。
         2.join()方法:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;接收一个参数，这个参数为数组元素的分隔符。
- 栈方法
           push():&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;接收任意多个参数，在数组末尾添加任意多项。
           返回数组的长度
- 队列方法
	       shift():&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;删除数组的第一项，并返回该项的值。
	       unshift():&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;接收任意多个参数，在数组的开头添加任意多项，
	       返回数组的长度。
- 重排序方法
	       reverse():&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;反转数组项的顺序
	       sort():&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;默认情况下按升序排列，但是可以接收比较函数。
	       比较函数&nbsp;&nbsp;&nbsp;如果第一个值位于第二个值的前面返回一个负数，
	       相等返回0，反之返回一个正数。
- 操作方法
	       concat():&nbsp;&nbsp;&nbsp;接收任意多个参数，创建一个新数组，该数组为原来数组的的副本。
	       将参数里的元素逐个添加到数组末尾。并返回新数组。
	       slice():&nbsp;&nbsp;&nbsp;接收一个或两个参数。第一个参数为起始位置，第二个参数为结束位置。
	       当只有一个参数时，默认为从起始位置到数组结束。返回新数组。
	       splice():&nbsp;&nbsp;&nbsp;接收2-3个参数。第一个参数为起始位置，第二个参数为数组的项数，
	       第三个参数为要添加给数组的字符串。
- 位置方法
	       indexOf()和lastIndexOf()都返回查找的项在数组中的起始位置。
	       可接收2个参数，分别是 查找的项和起始位置。indexOf()从数组开始查找，lastIndexOf()从数组末尾查找。
-迭代方法
	      every:&nbsp;&nbsp;&nbsp;对数组的每一项运行函数，当数组的每一项都返回true时，返回ture;
	      forEach():&nbsp;&nbsp;&nbsp;对数组的每一项运行函数，无返回值。
	      map():&nbsp;&nbsp;&nbsp;对数组的每一项运行函数，返回数组每项运行的结果组成的数组
	      some():&nbsp;&nbsp;&nbsp;对数组的每一项运行函数，当某一项返回true时，返回值是true
	      filter():&nbsp;&nbsp;&nbsp;对数组的每一项运行函数，返回返回值为true的项组成的数组
- 归并方法
	      reduce(),reduceRight():&nbsp;&nbsp;&nbsp;可接收4个参数，分别是：前一个值，
	      当前值，项的索引和数组对象。
	      reduce()从数组开头开始，第一项与第二项运行函数的返回值充当前一个值，再与数组的第三项运行函数...
	      reduceRight()只是从数组尾部开始运行函数。
	      <hr />
<h2>function类型</h2>
	 1.定义
	       函数定义有3种方法：分别是函数表达式，构造函数和 function name(){};
- function name	
	 	function fun(){
	       	return 0;
	     }
- 函数表达式
	 	var sum=function(a,b)
- 构造函数
    	var sum=new function("#","#",...)
		    **function构造函数可以接受任意多个参数，但是最后一个参数必须是函数体**
	2.函数重载
		     当同一个函数名定义了两个不同的函数体时，只对第二个函数体有效。因为第二个覆盖了第一个
	3.函数声明和函数表达式
		    在执行代码之前，解析器进行函数声明，javascript引擎第一遍会声明函数并将函数声明添加到执行环境中，
		    将函数声明置于源代码树的顶部。
		    如果用函数表达式法或构造函数法定义函数，则函数调用可置于函数声明之前。若为函数表达式，
		    则调用必须在声明之后。因为函数表达式当执行到它的代码行，它才会真正解析执行。
	4.函数的内部属性
    		 - arguement.callee :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    		 消除内部耦合,内部耦合即将递归函数名赋给一个变量a，将递归函数改变后，调用a它的函数值会改变
    		 - this :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;引用函数的环境对象，
    		 当在全局作用域执行函数时，this引用window。
    		 - caller :&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;调用当前函数的引用。
    		 在全局作用域调用当前函数，它的值为NULL.
    5.函数的属性及方法
 - 属性 
    length :&nbsp;&nbsp;&nbsp;表示接收的参数个数
    prototype :&nbsp;&nbsp;&nbsp;所有实例方法的真正所在。不可枚举。
 - 方法
    apply() :&nbsp;&nbsp;&nbsp;在特定的作用域调用函数，接收2个参数,
    	     分别是:函数的作用域，参数数组(arguement对象)。
    call() ：&nbsp;&nbsp;&nbsp;与apply()相同，不过接收参数的方式不同，将参数逐个列举出来。
    bind() :&nbsp;&nbsp;&nbsp;创建函数实例，将this值绑定到传入的参数上。 

<h2>Number类型</h2>
- toFixed() :&nbsp;&nbsp;&nbsp;接收一个数值参数，返回数字的指定小数位数的字符串表示。
- toString(),toLocalString() :&nbsp;&nbsp;&nbsp;返回字符串形式的数值。
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其中toString()可接收一个参数，它表示转化的基数。
- valueof()&nbsp;&nbsp;&nbsp;返回对象表示的基本类型的数值。
- toExponential() :&nbsp;&nbsp;&nbsp;返回指数表示。
- toPrecision() :&nbsp;&nbsp;&nbsp;返回数字的合适表示，可以是toFixed(),
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;也可以是toExponential().
<h2>Boolean类型</h2>
- Boolean类型是与布尔值相对应的引用类型。布尔表达式中的所有对象都会被转化为true.
- type对引用类型返回object,instanceof对引用类型返回true.
<h2>String类型</h2>
- 字符方法
  charAt :&nbsp;&nbsp;&nbsp;接收一个参数，即基于0的位置，返回该位置的字符。
  charCodeAt :&nbsp;&nbsp;&nbsp;与charAt()相同，返回该位置的字符的字符编码。
- 字符串操作方法
   1.concat() :&nbsp;&nbsp;&nbsp;上面已经描述过，不再赘述.
   2.sclice() :&nbsp;&nbsp;&nbsp;上面已经描述过，不再赘述.
   3.substr() :&nbsp;&nbsp;&nbsp；可以接收1-2个参数，分别是:&nbsp;&nbsp;&nbsp;起始位置，
   返回字符的个数。返回值是一个字符串或者一个字符。它会将第一个负值参数加上字符串长度
   得到一个正值，将第二个负值参数转化为0.
   4.substring() :&nbsp;&nbsp;&nbsp;接收1-2个参数，分别是:&nbsp;&nbsp;&nbsp;起始位置，
   结束位置。返回值是一个字符或字符串。它会把所有负值转化为0.
- 字符位置方法
   indexOf(),lastIndexOf() :&nbsp;&nbsp;&nbsp;上面已经描述过，不再赘述.
- trim()方法
   创建一个字符串的副本，删除字符串的前缀和后缀的所有空格，返回得到的字符串。
- 字符串大小写转化
    1.toLowerCase() :&nbsp;&nbsp;&nbsp;将所有字符转化为小写。
    2.toUpperCase() :&nbsp;&nbsp;&nbsp;将所有字符转化为大写。
    3.toLocalLowerCase(),toLocalUppercase():与上述两个作用相同，只是针对特定地区实现。
- 字符串模式匹配
   1.match() :&nbsp;&nbsp;&nbsp;接收一个参数，要么是正则表达式，要么是RegExp对象。返回一个数组。
   2.search() :&nbsp;&nbsp;&nbsp;接收参数与match()相同。返回字符串中第一个匹配项的索引。
   没有找到匹配项返回-1.
   3.replace() :&nbsp;&nbsp;&nbsp;接收2个参数。分别是 : 字符串(RegExp对象)和函数(字符串)。
   如果第一个参数是字符串，那么只会替换第一个子字符串。要想替换所有的字符串，就是将第一个
   参数设为正则表达式，且指定全局标志(g).
   4.localCompare() :&nbsp;&nbsp;&nbsp;比较两个字符串的大小。返回0，-1或1.
   5.fromCharCode() : 接收任意多个参数，它们是字符编码，返回与之对应的字符串。
**Date**
**Exe**