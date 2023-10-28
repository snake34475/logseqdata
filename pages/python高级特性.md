## 高级特性
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
		- list(range(1, 11))
		- 列表生成式
		- [结果 for 变量 in 列表(或元组等) 判断/循环]
		- ```python
		  [x * x for x in range(1, 11)]
		  [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
		  ```
	- ### generator 生成器（没看）
	- ### 迭代器（没看）