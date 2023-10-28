## 函数编程
	- ## 函数式编程
	  collapsed:: true
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
		- 其实可以理解为类似node的中间件的
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