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
	- 动态语言
		- [不要求严格的继承体系](https://www.liaoxuefeng.com/wiki/1016959663602400/1017497232674368)
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
	  collapsed:: true
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
	  collapsed:: true
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
  collapsed:: true
	- >每个包都有一个 `__init__py`文件，必须存在，否则会认为是普通目录而不是包
	- > 自己创建模块时要注意命名，不能和Python自带的模块名称冲突。例如，[[系统]]自带了sys模块，自己的模块就不可命名为sys.py，否则将无法导入[[系统]]自带的sys模块。
	-
	- ```python
	  #声明能在Unix/linux/Max上运行
	  #!/usr/bin/env python3
	  # 声明使用UTF-8编码
	  # -*- coding: utf-8 -*-
	  
	  #表示模块的文档注释，任何模块代码的第一个字符串都被视为模块的文档注释；
	  ' a test module '
	  
	  __author__ = 'Michael Liao'
	  
	  import sys
	  
	  def test():
	      args = sys.argv
	      if len(args)==1:
	          print('Hello, world!')
	      elif len(args)==2:
	          print('Hello, %s!' % args[1])
	      else:
	          print('Too many arguments!')
	  
	  if __name__=='__main__':
	      test()
	  ```
	- 特殊变量
		- `__xxx__`表示特殊变量，可以被直接引用，自己命名尽量不用用这种
	- 非公开变量
		- `_xxx`或`__xxx`不应该直接被引用
		- 不应该而不是不能，应该写一个函数去返回他们的值
- ## 面向对象（OOP）
  collapsed:: true
	- 特点 ：数据封装、继承和多态是面向对象的三大特点
	- ### 类和实例
		- 注意
			- 类内定义函数，第一个参数必定是他本身self
		- 案例
			- ```python
			  class Student(object):
			  
			      def __init__(self, name, score):
			          self.name = name
			          self.score = score
			  
			      def print_score(self):
			          print('%s: %s' % (self.name, self.score))
			  
			  bart = Student('Bart Simpson', 59)
			  ```
	- ### 访问限制
		- 在Python中，实例的变量名如果以`__`开头，就变成了一个私有变量（private），只有内部可以访问，外部不能访问
		- 注意：
			- 私有变量需要提供方法去修改和获取，目的是函数能进行检查避免无效参数
			- 本质上来说__xx或_x可以访问，但是为了代码严谨不应该访问
		- 案例：
			- ```python
			  class Student(object):
			      ...
			  
			      def set_score(self, score):
			          if 0 <= score <= 100:
			              self.__score = score
			          else:
			              raise ValueError('bad score')
			  ```
	- ### 继承多态
	  collapsed:: true
		- > 从当前class继承，新的class被称为子类（Subclass），而当前被称为基类，父类或超类（Base class，Super class）
		- 特点
			- 继承后有他的全部功能
			- 子类和父类有相同方法，子类覆盖父类
			- 多态，只要从同一父级派生，则参数填写其父级类型即可
			-
		- 判断是否属于某个类型
			- 子类也属于父类
			- ```python
			  >>> isinstance(a, list)
			  ```
		- ```python
		  class Dog(Animal):
		  
		      def run(self):
		          print('Dog is running...')
		  
		      def eat(self):
		          print('Eating meat...')
		  ```
	- ### 获取对象类型
	  collapsed:: true
		- type
			- 支持
				- 基本类型
				- 变量指向函数或者类
			- 返回的类型是Class类型
			- ```python
			  >>> type(123)
			  <class 'int'>
			  #比较
			  >>> type('abc')==type('123')
			  True
			  ```
			- 判断函数类型
				- ```python
				  >>> import types
				  >>> def fn():
				  ...     pass
				  ...
				  >>> type(fn)==types.FunctionType
				  True
				  >>> type(abs)==types.BuiltinFunctionType
				  True
				  >>> type(lambda x: x)==types.LambdaType
				  True
				  >>> type((x for x in range(10)))==types.GeneratorType
				  True
				  ```
		- isinstance
			- 能用`type()`判断的基本类型也可以用`isinstance()`判断：
			- 判断一个变量是否是某些类型中的一种
			- >总是优先使用isinstance()判断类型，可以将指定类型及其子类“一网打尽”。
		- dir 获取对象所有的属性和方法
			- ```python
			  >>> dir('ABC')
			  ['__add__', '__class__',..., '__subclasshook__', 'capitalize', 'casefold',..., 'zfill']
			  ```
		- 其他
			- ```python
			  >>> hasattr(obj, 'x') # 有属性'x'吗？
			  True
			  >>> obj.x
			  9
			  >>> hasattr(obj, 'y') # 有属性'y'吗？
			  False
			  >>> setattr(obj, 'y', 19) # 设置一个属性'y'
			  >>> hasattr(obj, 'y') # 有属性'y'吗？
			  True
			  >>> getattr(obj, 'y') # 获取属性'y'
			  19
			  >>> obj.y # 获取属性'y'
			  19
			  >>> getattr(obj, 'z', 404) # 获取属性'z'，如果不存在，返回默认值404
			  404
			  ```
	- ### 实例属性和对象
	-
- ## 面向对象高级编程
  collapsed:: true
	- ###  动态添加方法
		- #### 类添加
		  collapsed:: true
			- ```python
			  >>> def set_score(self, score):
			  ...     self.score = score
			  ...
			  >>> Student.set_score = set_score
			  ```
		- #### 实例添加
		  collapsed:: true
			- ```python
			  >>> def set_age(self, age): # 定义一个函数作为实例方法
			  ...     self.age = age
			  ...
			  >>> from types import MethodType
			  >>> s.set_age = MethodType(set_age, s) # 给实例绑定一个方法
			  >>> s.set_age(25) # 调用实例方法
			  >>> s.age # 测试结果
			  25
			  ```
	- ### 限制实例的属性
	  collapsed:: true
		- 仅对当前实例有用
		- ```python
		  >>> s = Student() *# 创建新的实例*
		  >>> s.name = 'Michael' *# 绑定属性'name'*
		  >>> s.age = 25 *# 绑定属性'age'*
		  >>> s.score = 99 *# 绑定属性'score'*
		  Traceback (most recent call last):
		    File "<stdin>", line 1, **in** <module>
		  AttributeError: 'Student' object has no attribute 'score'
		  ```
	- 后续没有看（等候补）
- ## 异常
  collapsed:: true
	- 错误处理
		- try
		  collapsed:: true
			- 成功的话不执行except
			- 不成中断，执行except和其他的
			- ```python
			  try:
			      print('try...')
			      r = 10 / 0
			      print('result:', r)
			  except ZeroDivisionError as e:
			      print('except:', e)
			  finally:
			      print('finally...')
			  print('END')
			  ```
	- 调试
		- 断言
		- logging
			- ```python
			  import logging
			  logging.basicConfig(level=logging.INFO)
			  
			  s = '0'
			  n = int(s)
			  logging.info('n = %d' % n)
			  print(10 / n)
			  ```
			- `logging.info()`
		-
- ## IO编程
	- ###  文件读写
	  collapsed:: true
		- ```python
		  #r表示读
		  f = open('/Users/michael/test.txt', 'r')
		  #读到内存中
		  f.read()
		  #隔壁文件，因为会占用操作系统资源
		  f.close()
		  
		  #二进制文件，图片，视频等等
		  >>> f = open('/Users/michael/test.jpg', 'rb')
		  ```
		- 通常写法，python自己调用close关闭
			- ```python
			  with open('/path/to/file', 'r') as f:
			      print(f.read())
			      
			  #w 没有就新建， a的话是追加
			  with open('/Users/michael/test.txt', 'w') as f:
			      f.write('Hello, world!')
			  ```
		- 注意
			- ```python
			  #r表示读
			  f = open('/Users/michael/test.txt', 'r')
			  
			  
			  #读到内存中
			  f.read()
			  #隔壁文件，因为会占用操作系统资源
			  f.close()
			  ```
	- ### 缓存
		- #### StingIO
		  collapsed:: true
			- ```python
			  ## 写入
			  form io import StringIO
			  f=StringIO()
			  f.write("hellow")
			  print(f.getvalue())
			  
			  #读取
			  form io import StringIO
			  f=StringIO('Hello!\nHi!\nGoodbye!')
			  while True:
			    s=f.readline()
			    if s=='':
			      break
			    print(s.strip())
			  ```
		- #### BytesIO
		  collapsed:: true
			- ```python
			  form io import BytesIO
			  f=BytesIO()
			  f.write("中文".encode("utf-8"))
			  print(f.getvalue())
			  
			  >>> from io import BytesIO
			  >>> f = BytesIO(b'\xe4\xb8\xad\xe6\x96\x87')
			  >>> f.read()
			  ```
	- ### 操作文件目录
		- ```python
		  >>> import os
		  >>> os.name # 操作系统类型
		  >>> os.environ #环境变量
		  >>> os.environ.get('PATH') #获取某个特定的值
		  
		  
		  # 查看当前目录的绝对路径:
		  >>> os.path.abspath('.')
		  '/Users/michael'
		  # 在某个目录下创建一个新目录，首先把新目录的完整路径表示出来:
		  >>> os.path.join('/Users/michael', 'testdir')
		  '/Users/michael/testdir'
		  # 然后创建一个目录:
		  >>> os.mkdir('/Users/michael/testdir')
		  # 删掉一个目录:
		  >>> os.rmdir('/Users/michael/testdir')
		  #拆分路径
		  >>> os.path.split('/Users/michael/testdir/file.txt')
		  ('/Users/michael/testdir', 'file.txt')
		  #os.path.splitext()可以直接让你得到文件扩展名
		  >>> os.path.splitext('/path/to/file.txt')
		  ('/path/to/file', '.txt')
		  
		  ##列出所当前目录下所有文件
		  >>> [x for x in os.listdir('.') if os.path.isdir(x)]
		  #要列出所有的.py文件
		   [x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1]=='.py']
		  ```
-
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