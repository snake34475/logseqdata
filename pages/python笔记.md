- #python
- {{renderer :tocgen2, [[python笔记]]}}
-
- ## 规范
	- 始终坚持四个空格的缩进
	- 头部
	  collapsed:: true
		- ```python
		  #!/usr/bin/env python3
		  # -*- coding: utf-8 -*-
		  ```
- ## 输入输出
	- ```python
	  name = input('please enter your name: ')
	  print('hello,', name)
	  
	  ```
- ## 数据类型
	- 整数
	- 浮点数
	- 字符串
	  collapsed:: true
		- 占位符
		  collapsed:: true
			- | 占位符 | 替换内容 |
			  | ---- | ---- | ---- |
			  | %d | 整数 |
			  | %f | 浮点数 |
			  | %s | 字符串 |
			  | %x | 十六进制整数 |
			- ```python
			  print("我是 %s" %"王腾瑶")
			  ```
		- format()格式化
		  collapsed:: true
			- ```python
			  >>> 'Hello, {0}, 成绩提升了 {1:.1f}%'.format('小明', 17.125)
			  'Hello, 小明, 成绩提升了 17.1%'
			  ```
		- f-string （常用）
		  collapsed:: true
			- ```python
			  >>> r = 2.5
			  >>> s = 3.14 * r ** 2
			  >>> print(f'The area of a circle with radius {r} is {s:.2f}')
			  The area of a circle with radius 2.5 is 19.62
			  #上述代码中，{r}被变量r的值替换，{s:.2f}被变量s的值替换，并且:后面的.2f指定了格式化参数（即保留两位小数），因此，{s:.2f}的替换结果是19.62。
			  ```
		- code码互转
		  collapsed:: true
			- ```python
			  >>> ord('A')
			  65
			  >>> ord('中')
			  20013
			  >>> chr(66)
			  'B'
			  >>> chr(25991)
			  '文'
			  ```
		- len() 获取长度
	- 布尔值
	  collapsed:: true
		- True
		- False
	- 空值
	  collapsed:: true
		- None
	- 常量
	  collapsed:: true
		- PI也就是3.1415926
	- list 列表
	  collapsed:: true
		- 长度元素可变
		- 方法
			- len()获取长度
			- 获取最后一个
			  collapsed:: true
				- ```python
				  >>> classmates[-1]
				  'Tracy'
				  ```
			- append 尾部追加
			  collapsed:: true
				- ```
				  >>> classmates.append('Adam')
				  >>> classmates
				  ['Michael', 'Bob', 'Tracy', 'Adam']
				  ```
			- insert 插入
			  collapsed:: true
				- ```
				  >>> classmates.insert(1, 'Jack')
				  >>> classmates
				  ['Michael', 'Jack', 'Bob', 'Tracy', 'Adam']
				  ```
			- pop
			  collapsed:: true
				- 直接使用是删除末尾
				- 有参数是删除下标第几个
			- 替换
			  collapsed:: true
				- 使用下标替换
			- range(num) 生成0到num的序列
			-
	- tuple 元组
	  collapsed:: true
		- tuple和list非常类似，但是tuple一旦初始化就不能修改
		      不可变的tuple有什么意义？因为tuple不可变，所以代码更安全。如果可能，能用tuple代替list就尽量用tuple。
		- 例子
		  collapsed:: true
			- 无参数
			  ```
			  >>> t = ()
			  >>> t
			  ()
			  ```
			- 一个参数
			  ```
			  >>> t = (1,)
			  >>> t
			  (1,)
			  ```
			- 两个参数
			  ```
			  >>> t = (1, 2)
			  >>> t
			  (1, 2)
			  ```
		-
	- dict 字典
	  collapsed:: true
		- 对比dict特点
			- 查找和插入的速度极快，不会随着key的增加而变慢；
			- 需要占用大量的内存，内存浪费多。
		- 方法
			- in 判断存在
			- get获取值
			- pop 删除
				- 注意，这个参数必传，要不会报错
		- 注意
		  collapsed:: true
			- > 请务必注意，dict内部存放的顺序和key放入的顺序是没有关系的。
			- key不存在会报错
				- in方法进行判断
				  ```python
				  >>> 'Thomas' in d
				  False
				  ```
				- get 方法
				  ```python
				  >>> d.get('Thomas')
				  none
				  >>> d.get('Thomas', -1)#自定义返回值，如果不存在就返回-1
				  -1
				  ```
		-
	- set
	  collapsed:: true
		- key的集合，不存value
		- 方法
			- add
				- ```
				  >>> s.add(4)
				  >>> s
				  {1, 2, 3, 4}
				  >>> s.add(4)
				  >>> s
				  {1, 2, 3, 4}
				  ```
			- remove
				- ```
				  >>> s.remove(4)
				  >>> s
				  {1, 2, 3}
				  ```
			- &和 | 做交集和并集
				- ```
				  >>> s1 = set([1, 2, 3])
				  >>> s2 = set([2, 3, 4])
				  >>> s1 & s2
				  {2, 3}
				  >>> s1 | s2
				  {1, 2, 3, 4}
				  ```
		- 例子
			- ```
			  >>> s = set([1, 1, 2, 2, 3, 3])
			  >>> s
			  {1, 2, 3}
			  ```
		-
	- 函数
		- [官方文档](https://docs.python.org/3/library/functions.html#abs)
		- 如果有必须要需要对函数进行类型检查
			- ```python
			  
			  def my_abs(x):
			      if not isinstance(x, (int, float)):
			          raise TypeError('bad operand type')
			      if x >= 0:
			          return x
			      else:
			          return -x
			  ```
		- 可以返回多个值，多个值返回的是元组
			- ```python
			  >>> r = move(100, 100, 60, math.pi / 6)
			  >>> print(r)
			  (151.96152422706632, 70.0)
			  ```
		- 例子
			- 无参数
			  ```python
			  def nop():
			      pass
			  ```
- ## 运算符号
  collapsed:: true
	- 逻辑运算
		- and
		- or
		- not
	- 算数运算
		- `/`
			- 结果是浮点数
			- ```
			  >>> 9 / 3
			  3.0
			  ```
		- `//`
			- 地板除，相当于取余
			- ```
			  >>> 10 // 3
			  3
			  ```
		- `%`
			- 取余数
- 条件判断
  collapsed:: true
	- if
		- ```
		  age = 3
		  if age >= 18:
		      print('adult')
		  elif age >= 6:
		      print('teenager')
		  else:
		      print('kid')
		  ```
	-
- 异常
	- ```python
	  def my_abs(x):
	      if not isinstance(x, (int, float)):
	          raise TypeError('bad operand type')
	      if x >= 0:
	          return x
	      else:
	          return -x
	  ```