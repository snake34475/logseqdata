## 模块
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
	- ###  动态添加方法
		- #### 类添加
			- ```python
			  >>> def set_score(self, score):
			  ...     self.score = score
			  ...
			  >>> Student.set_score = set_score
			  ```
		- #### 实例添加
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