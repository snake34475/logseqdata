- unity常用方法
	- [手把手进度条](https://blog.csdn.net/weixin_45375968/article/details/123754722)
	- [什么是(携程)IEnumerator](https://blog.csdn.net/beihuanlihe130/article/details/76098844)
		- 调用携程的时候，不要将执行函数的对象设置为不可见，否则不会执行
	- [[数据库]]
	  collapsed:: true
		- [数据库动态链](https://juejin.cn/post/6997660118032597029)
			- 他的动态链引入可能会有问题，应该去
			- ```js
			  \Editor\Data\MonoBleedingEdge\lib\mono\unityjit这个文件中将文件粘过来不会报错
			  ```
			- [data.dll地址](https://cn.dll-files.com/mysql.data.dll.html) 通过status查看当前mysql的状态
			- [unity mysql踩坑日记](https://blog.csdn.net/qq_41692884/article/details/121958055)
		- [登录sql](https://zhuanlan.zhihu.com/p/498490650)
		- ```
		  Client does not support authentication protocol requested by server; consider upgrading MySQL client"
		  
		  连接mysql8.0一直提示异常，尝试了下低版本的可以
		  //进入mysql之后，执行一下命令即可降级8.0的身份验证方式从而成功连接
		  ALTER USER 'username'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
		  ```
			-
			-
	- 热更新
		- [huato](https://hybridclr.doc.code-philosophy.com/docs/beginner/quickstart)
			- 常见问题
				- 需要从vsinstall中重装c++，需要从unity中装IL2CCP
-