- #原型链
	- ## 什么是原型链
		- https://images2018.cnblogs.com/blog/1265396/201711/1265396-20171127082821065-1506469155.png
		- 原型对象是用于实现对象继承和共享的一种机制，更简单来说原型对象只是一个普通的对象，包含共享的属性和方法，可以被其他对象所共享
		- 所以说要给prototype添加
	- ## constructor原理
		- ```js
		  var M = function(name){this.name = name;}
		  var o3 = new M('o3')
		  //
		  ```
	- ## instanceof原理
		- https://images2018.cnblogs.com/blog/1265396/201711/1265396-20171127092153300-1935600767.png
		- instanceof原理是判断实例对象的_proto_与生成该实例的构造函数的prototype是否为同一地址
	- ## null是原型链的末端
		- ```js
		  [] instanceof Array //true
		  [] instanceof Object //true
		  [] instanceof null //false
		  ```
		- 为什么第三个是false，因为instanceof是通过_proto_与prototype的引用地址进行对比的，但是null位于原型链的顶端没有prototype不存在原型对象
	- ## 文章参考
		- 文章链接[详谈JavaScript原型链](https://www.cnblogs.com/chengzp/p/prototype.html)
-