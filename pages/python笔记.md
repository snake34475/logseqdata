- #python
-
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
	- ### 整数
	- ### 浮点数
	- ### 字符串
	  collapsed:: true
		- [字符串方法](https://docs.python.org/3/library/stdtypes.html#string-methods)
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
		- lower() 小写
		- script()清空空格
		- isinstance(item,str) 判断是否为字符串类型
		-
	- ### 布尔值
	  collapsed:: true
		- True
		- False
	- ### 空值
	  collapsed:: true
		- None
	- ### 常量
	  collapsed:: true
		- PI也就是3.1415926
	- ### list 列表
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
	- ### tuple 元组
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
	- ### dict 字典
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
	- ### set
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
	- ### 函数
		- [官方文档](https://docs.python.org/3/library/functions.html#abs)
		- 使用属性名称传参
		  collapsed:: true
			- ```python
			  def enroll(name, gender, age=6, city='Beijing'):
			      print('name:', name)
			      print('gender:', gender)
			      print('age:', age)
			      print('city:', city)
			  ```
		- 默认值
		  collapsed:: true
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
		  collapsed:: true
			-
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
		- 关键字参数
		  collapsed:: true
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
		- 返回多个值
		  collapsed:: true
			- 多个值返回的是元组
			- ```python
			  >>> r = move(100, 100, 60, math.pi / 6)
			  >>> print(r)
			  (151.96152422706632, 70.0)
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
- ## 高级特性
	- ### 取片
		- 可以操作字符串，元组，数组
		- ```python
		  >>> L[0:3]
		  ['Michael', 'Sarah', 'Tracy']
		  
		  >>> L[:3]
		  ['Michael', 'Sarah', 'Tracy']
		  #没间两个取一个
		  >>> L[:10:2]
		  [0, 2, 4, 6, 8]
		  ```
	- ### 迭代
	  collapsed:: true
		- 数组 下标+值
			- ```python 
			  >>> for i, value in enumerate(['A', 'B', 'C']):
			  ...     print(i, value)
			  ...
			  0 A
			  1 B
			  2 C
			  ```
	- ### 列表生成
	  collapsed:: true
		- list(range(1, 11))
		- 列表生成式
		- [结果 for 变量 in 列表(或元组等) 判断/循环]
		- ```python
		  [x * x for x in range(1, 11)]
		  [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
		  ```
	- ### generator 生成器（没看）
	- ### 迭代器（没看）
- ## 函数编程
  collapsed:: true
	- ## 函数式编程
		- 任意一个函数，只要输入是确定的，输出就是确定的，这种纯函数我们称之为没有副作用。
		- 允许把函数本身作为参数传入另一个函数，还允许返回一个函数！
	- ## 高阶函数
		- ### map/reduce
			- ```python
			  #map
			  >>> list(map(str, [1, 2, 3, 4, 5, 6, 7, 8, 9]))
			  ['1', '2', '3', '4', '5', '6', '7', '8', '9']
			  #reduce
			  >>> from functools import reduce
			  >>> def add(x, y):
			  ...     return x + y
			  ...
			  >>> reduce(add, [1, 3, 5, 7, 9])
			  25
			  ```
		- ### filter
			- `filter()`把传入的函数依次作用于每个元素，然后根据返回值是`True`还是`False`决定保留还是丢弃该元素。
			- ```python
			  def not_empty(s):
			      return s and s.strip()
			  
			  list(filter(not_empty, ['A', '', 'B', None, 'C', '  ']))
			  # 结果: ['A', 'B', 'C']
			  ```
		- ### sorted
			- ```python
			  #支持传入key参数实现自定义潘旭
			  >>> sorted([36, 5, -12, 9, -21], key=abs)
			  [5, 9, -12, -21, 36]
			  
			  #第三个参数反向查询
			  >>> sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower, reverse=True)
			  ['Zoo', 'Credit', 'bob', 'about']
			  ```
	- ## 返回函数(闭包)
	- ## 匿名函数
		- ```python
		  >>> list(map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9]))
		  [1, 4, 9, 16, 25, 36, 49, 64, 81]
		  ```
		-
	- ## 装饰器
	  collapsed:: true
		- > 在代码运行旗舰动态增加功能的方式，被称为"装饰器"（Decorator）。
		- 无参数
			- ```python
			  #定义装饰器
			  import functools
			  def log(func):
			    #将其他属性复制到当前的函数中去
			    @functools.wraps(func)
			    def wrapper(*args,**kw):
			        print("call *%s* ():" % func.__name__ )
			        return func(*args,**kw)
			    return wrapper
			  #注册装饰器
			  @log
			  def now():
			    print("2023-5-15")
			  
			  f=now
			  f()
			  print(now.__name__)
			  #wrapper
			  #类似于 now = log(now)
			  ```
		- 有参数
			- ```python
			  import functools
			  def logtwo(text):
			      def decorator(func):
			          @functools.wraps(func)
			          def wrapper(*args,**kw):
			              print("%s %s ():" % (text,func.__name__) )
			              return func(*args,**kw)
			          return wrapper
			      return decorator
			  # @log
			  @logtwo("打印出来的错误是：")
			  def now():
			      print("2023-5-15")
			  
			  f=now
			  
			  f()
			  print(now.__name__)
			  #>>> now = log('execute')(now)
			  ```
		- 测试函数执行时间
			- ```python
			  def metric(func):
			         @functools.wrapper(func)
			         def wrapper(*args,**kw):
			             start_time=time.time()
			             result = func(*args, **kw)
			             end_time=time.time()
			             print("时间： %s" % (end_time-start_time))
			             return result
			         return wrapper
			  
			  
			  # 测试
			  @metric
			  def fast(x, y):
			      time.sleep(0.0012)
			      return x + y;
			  
			  @metric
			  def slow(x, y, z):
			      time.sleep(0.1234)
			      return x * y * z;
			  
			  f = fast(11, 22)
			  s = slow(11, 22, 33)
			  if f != 33:
			      print('测试失败!')
			  elif s != 7986:
			      print('测试失败!')
			  
			  ```
	- ## 偏函数
		- >通过设定参数的默认值，可以降低函数调用的难度。
		- ```python
		  #使用自带的functools.partial函数构建一个偏函数
		  >>> import functools
		  >>> int2 = functools.partial(int, base=2)
		  >>> int2('1000000')
		  64
		  >>> int2('1010101')
		  85
		  ```
- ## 模块
	- >每个包都有一个 `__init__py`文件，必须存在，否则会认为是普通目录而不是包
	- > 自己创建模块时要注意命名，不能和Python自带的模块名称冲突。例如，[[系统]]自带了sys模块，自己的模块就不可命名为sys.py，否则将无法导入[[系统]]自带的sys模块。
	-
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
	- if
		- ```python
		  age = 3
		  if age >= 18:
		      print('adult')
		  elif age >= 6:
		      print('teenager')
		  else:
		      print('kid')
		  ```
	-
- 三目表达式
	- ```python
	  value= True if a>b else False
	  #如果为true就返回前面的，为false就是后面的
	  ```
- 异常
  collapsed:: true
	- ```python
	  def my_abs(x):
	      if not isinstance(x, (int, float)):
	          raise TypeError('bad operand type')
	      if x >= 0:
	          return x
	      else:
	          return -x
	  ```