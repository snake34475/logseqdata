## 数据类型
	- ### 整数
	- ### 浮点数
	- ### 字符串
		- [字符串方法](https://docs.python.org/3/library/stdtypes.html#string-methods)
		- 占位符
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
			- ```python
			  >>> 'Hello, {0}, 成绩提升了 {1:.1f}%'.format('小明', 17.125)
			  'Hello, 小明, 成绩提升了 17.1%'
			  ```
		- f-string （常用）
			- ```python
			  >>> r = 2.5
			  >>> s = 3.14 * r ** 2
			  >>> print(f'The area of a circle with radius {r} is {s:.2f}')
			  The area of a circle with radius 2.5 is 19.62
			  #上述代码中，{r}被变量r的值替换，{s:.2f}被变量s的值替换，并且:后面的.2f指定了格式化参数（即保留两位小数），因此，{s:.2f}的替换结果是19.62。
			  ```
		- code码互转
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
		- lower() 小写
		- script()清空空格
		- isinstance(item,str) 判断是否为字符串类型
	- ### 布尔值
		- True
		- False
	- ### 空值
		- None
	- ### 常量
		- PI也就是3.1415926
	- 数据类型转换
		- ```python
		  >>> int('123')
		  123
		  >>> int(12.34)
		  12
		  >>> float('12.34')
		  12.34
		  >>> str(1.23)
		  '1.23'
		  >>> str(100)
		  '100'
		  >>> bool(1)
		  True
		  >>> bool('')
		  False
		  
		  ```
	- ### list 列表
		- 长度元素可变
		- 方法
			- len()获取长度
			- 替换
			  collapsed:: true
				- 使用下标替换
			- range(num) 生成0到num的序列
			- ```python
			  >>> classmates[-1] //获取最后一个
			  'Tracy'
			  classmates.append('Adam')
			  classmates.insert(1, 'Jack')
			  classmates.pop()
			   classmates.pop(1) //删除指定的，不填删除最后一个
			  ```
			-
	- ### tuple 元组
		- tuple和list非常类似，但是tuple一旦初始化就不能修改
		      不可变的tuple有什么意义？因为tuple不可变，所以代码更安全。如果可能，能用tuple代替list就尽量用tuple。
		- 例子
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
	- ### dict 字典
		- 对比dict特点
			- 查找和插入的速度极快，不会随着key的增加而变慢；
			- 需要占用大量的内存，内存浪费多。
			- ```python
			  d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
			  ```
		- 方法
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
	- ### set
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
	- ### 函数
		- [官方文档](https://docs.python.org/3/library/functions.html#abs)
		- 使用属性名称传参
			- ```python
			  def enroll(name, gender, age=6, city='Beijing'):
			      print('name:', name)
			      print('gender:', gender)
			      print('age:', age)
			      print('city:', city)
			  ```
		- 默认值
			- 调用多次后发现返回结果不一致
			  ```python
			  def add_end(L=[]):
			      L.append('END')
			      return L
			  >>> add_end() 
			  ['END']
			  >>> add_end()
			  ['END', 'END']
			  >>> add_end()
			  ['END', 'END', 'END']
			  ```
			- 原因：在python中，如果默认参数是一个可变对象，那么这个参数在函数定义的时候就被创建，而不是每次重新建一个，不变对象有none或str
			  而js中是每次都新建一个list
			- 修改后:
			  ```python
			  def add_end(L=None):
			      if L is None:
			          L = []
			      L.append('END')
			      return L
			  ```
		- 可变参数
			- 此后可以传入任意多个参数，包括0个参数
			  ```python
			  def calc(*numbers):
			      sum = 0
			      for n in numbers:
			          sum = sum + n * n
			      return sum
			  #传入元组或列表也可以使用这种方法
			  nums=[1,2,3]
			  calc(*nums)
			  ```
		- 关键字参数，简单的说就是之后的所有的参数
			- kw获得的dict是extra的一份拷贝，其改动并不会影响函数外的extra
			  ```python
			  def person(name, age, **kw):
			      print('name:', name, 'age:', age, 'other:', kw)
			      
			  >>> person('Jack', 24, **extra)
			  name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
			  ```
			- 命名关键字
				- 需要添加一个特殊的分隔符，*之后的参数并命名为命名关键字参数
				  ```python
				  def person(name, age, *, city, job):
				      print(name, age, city, job)
				  ```
				- 如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符`*`了：
				  ```python
				  def person(name, age, *args, city, job):
				      print(name, age, args, city, job)
				  ```
		- 类型检查
		  collapsed:: true
			- 如果有必须要需要对函数进行
			- ```python
			  
			  def my_abs(x):
			      if not isinstance(x, (int, float)):
			          raise TypeError('bad operand type')
			      if x >= 0:
			          return x
			      else:
			          return -x
			  ```
		- 返回
			- 返回多个值
				- 多个值返回的是元组
				- ```python
				  r = move(100, 100, 60, math.pi / 6)
				  print(r)
				  (151.96152422706632, 70.0)#返回元组
				  
				  x, y = move(100, 100, 60, math.pi / 6)
				  print(x, y)
				  151.96152422706632 70.0 #类似于js的解构赋值
				  ```
			- 没有返回值要写pass防止报错
				- ```python
				  def nop():
				    pass
				  ```
		- 例子
		  collapsed:: true
			- 无参数
			  ```python
			  def nop():
			      pass
			  ```
		- 小结
			- `*args`是可变参数，args接收的是一个tuple；
			- `**kw`是关键字参数，kw接收的是一个dict。