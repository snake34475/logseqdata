- #python
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
- ## 常用片段
	- ```python
	  name = input('please enter your name: ')
	  print('hello,', name)
	  
	  #三目表达式
	  value= True if a>b else False
	  
	  #算数运算
	  not and  or
	  
	  #取浮点数
	  >>> 9 / 3
	  3.0 
	  
	  #地板除，取整数
	  >>> 10 // 3
	  3 
	  
	  
	  ```
- ## 异常
	- 错误处理
		- try
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
- ## 访问[[数据库]]
	- ## SQLite
		- {{embed [[SQLite]]}}
- ## 实战类
	- 1.搭建web APP骨架
	- 2.[[数据库]]
		- 创建连接池（关于连接池可以看这里[[连接池]]）
			-
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