- 路由
  * get
  * post
  * all
- 托管静态文件
  ```js
  	app.use( express.static('public'))  
  
  	//赋予别名  记得别忘了下划线 
  	//正确
       app.use('/static', express.static('public'))
  	//错误
  	app.use('static', express.static('public'))
  ```
  > 此时public下有文件1.png，则可以通过`localhost:port/1.png`或`localhost:port/static/1.png`进行访问
- 中间件
  可以做通用且非业务逻辑的功能，通常是 客户端-》url请求-》中间件-》请求-》服务器主逻辑处理
  * 记录所有请求日志
  * 身份验证
- 错误处理
-