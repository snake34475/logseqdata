- unity常用方法
	- json
		- ```C#
		  string str = JsonUtililty.ToJson();
		  A a = JsonUtility.FromJson<A>(str)
		  ```
	- [手把手进度条](https://blog.csdn.net/weixin_45375968/article/details/123754722)、
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
		  
		  ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '8700188'
		  ```
			-
	- 获取不到初始active为false的物体
		- 可以通过transform获取到
		- ```
		  GameObject.Find("Main Camera").transform.Find("登录").gameObject.SetActive(true);
		  ```
	- 热更新
		- [huato](https://hybridclr.doc.code-philosophy.com/docs/beginner/quickstart)
			- 常见问题
				- 需要从vsinstall中重装c++，需要从unity中装IL2CCP
	- 常用方法
		- ```c#
		  //数组转化成字符串
		  new string()
		  .ToString();
		  
		  //转化成整数
		  int.Parse();
		  
		  //字符串转化成数组
		  .ToCharArray();
		  
		  string.Empty; //空字符串
		  Count适用于集合，list，hashset
		  length用于数组，字符串
		  
		  //资源加载
		  Resource.Load(); //加载resources目录
		  AssetBundle.loadFromXXX(); //加载asset bundle
		  UnityEditor.AssetDatabase.LoadAssetAtPath(); //加载其他文件夹
		  ```
	- 开发收藏文章
		- [# 手把手教你C#如何使用SqlSugar操作MySQL数据库](https://blog.csdn.net/qq_42461824/article/details/128824999)
		- [多人聊天室](https://blog.csdn.net/qq_42461824/article/details/85646260)
- 关键词汇
	- 状态机
	- 行为树 [csdn](https://blog.csdn.net/flyTie/article/details/126440816)
	- 热更新
		- huato
	- 多人联机
		- 插件
			- [[Unity]] Multiplay 官网
			- Photon [[Unity]] Networking（PUN） 多人联机的unity插件，不用搭建服务端 免费同时20个人同时连接
			- Mirror 免费
			- 自定义
	- 骨骼
	- 泛型
		- defult关键词 不清楚类型参数为引用类型还是值类时使用
		- where:new()含义
			- 参数类型限制，表示必须为没有参数的构造函数
			-
			- ```
			  where T:strust //必须是结构类型
			  where T:class //必须是一个class类型
			  where T:new() //必须要有一个无参数构造类型
			  where T:NameOfBaseClass 必须继承名为NameOfClass的类
			  ```