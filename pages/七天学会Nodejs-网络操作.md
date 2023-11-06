- 注意！！
	- header访问的请求头不是驼峰的，为了统一都转换成了小写字母格式`headers['content-length']`。
	- http响应为什么是chunked传输，因为默认情况下没有限制content-Length就不确定相应长度，所以使用chunked传输，如果设定长度，就不会使用
- 总结
	- http和https支持服务端和客户端两种方式
	- request和response可以读写头数据和数据流
	- url.parse和request用于http的固定搭配
	- zlib支持压缩
	- net用于socket链接
-
- 外援！！
	- {{embed ((6544885a-7b02-427d-98ca-9335bbe45e53))}}
	-
- http基础请求
	- 操作响应
		- ```js
		  var http = require('http')
		  
		  http.createServer(function(req,res){
		      //写响应头 类容类型
		      res.writeHead(200,{'Content-Type':'text-plain'})
		      //写响应体
		      res.end("Hello world")
		  }).listen(8124)//就是开了个端口监听，每次来请求，就会调用相应的回调函数
		  ```
	- 操作请求和响应
		- 为什么监听request的数据去执行write，因为数据是分块传输的
		- ```js
		  http.createServer(function(req,res){
		      var body = []
		  
		      console.log(req.method)//打印请求方法
		      console.log(req.headers)//打印请求头
		  
		      //接收到数据时触发
		      //当客户端发送数据时，数据会被分成多个数据块（chunk）进行传输。因此，我们需要在接收到每个数据块时进行处理，而不是一次性接收所有数据。
		      req.on('data',function(chunk){
		          body.push(chunk)
		          response.write(chunk);//将请求写入响应体
		      })
		  
		      //数据接收完毕后触发
		      req.on('end',function(){
		          body = Buffer.concat(body)
		          console.log(body.toString())
		          res.end()//关闭http请求
		      })
		  
		      
		      //写响应头
		      res.writeHead(200,{'Content-Type':'text-plain'})
		      //写响应体
		      res.end("Hello world")
		  }).listen(8124)//就是开了个端口监听，每次来请求，就会调用相应的回调函数
		  ```
- https
	- 需要额外处理ssl整数
	- ```js
	  //https请求
	  var options = {
	          key: fs.readFileSync('./ssl/default.key'),
	          cert: fs.readFileSync('./ssl/default.cer'),
	    rejectUnauthorized:false//可以禁用对证书有效性的检查
	      };
	  
	  var server = https.createServer(options, function (request, response) {
	          // ...
	      });
	  
	  //添加多个证书
	  server.addContext('foo.com', {
	      key: fs.readFileSync('./ssl/foo.com.key'),
	      cert: fs.readFileSync('./ssl/foo.com.cer')
	  });
	  
	  server.addContext('bar.com', {
	      key: fs.readFileSync('./ssl/bar.com.key'),
	      cert: fs.readFileSync('./ssl/bar.com.cer')
	  });
	  ```
- URL
	- url的组成
		- ```js
		                             href
		   -----------------------------------------------------------------
		                              host              path
		                        --------------- ----------------------------
		   http: // user:pass @ host.com : 8080 /p/a/t/h ?query=string #hash
		   -----    ---------   --------   ---- -------- ------------- -----
		  protocol     auth     hostname   port pathname     search     hash
		                                                  ------------
		                                                     query
		  ```
		- protocol: 协议，如http或https。
		- auth：认证信息
		- hostname主机名
		- prot端口
		- pathname路径名称
		- search 查询参数
		- hash 锚点
	- 常用方法
		- ```js
		  //老版本
		   let url1 = url.parse("http://user:pass@host.com:8080/p/a/t/h?query=string#hash")
		  console.log(url1.query)//获取query query=string
		  
		  // let url1 = url.parse("http://user:pass@host.com:8080/p/a/t/h?query=string#hash"，true)
		  //能将获取的query进行对象话
		  
		  //新版本
		  let url2 = new URL('http://user:pass@host.com:8080/p/a/t/h?query=string#hash')
		  console.log('ur2:',url2.searchParams.get('query'))
		  console.log('ur2:')
		  
		  //format转化成url
		  const url3 = {
		      protocol:'http:',
		      host:"snake34475.github.io",
		      pathname:'/logseqdata',
		      search:""
		  }
		  console.log("转化成url：",url.format(url3))
		  
		  //url转化成对象
		  const urlString = 'https://www.example.com/path?foo=bar&baz=qux';
		  const parsedUrl = new URL(urlString);
		  const queryParams = parsedUrl.searchParams;
		  const paramsObject = Object.fromEntries(queryParams.entries());
		  ```
- queryString（旧版本使用较多，常用于旧版本的解压）
	- ```js
	  //querystring 通常用于url参数对象互转
	  querystring.parse('foo=bar&baz=qux&baz=quux&corge');
	  querystring.stringify({ foo: 'bar', baz: ['qux', 'quux'], corge: '' });
	  
	  //旧版本中可以这么使用
	  var url = require('url')
	  var queryString = require('queryString')
	  var url1 = url.parse('http://user:pass@host.com:8080/p/a/t/h?query=string#hash')
	  var obj =queryString(url1.query) 
	  ```
- zlib 数据压缩和解压
	- 服务端压缩响应
		- 判断客户端响应是否支持压缩
	- 客户端解压响应
		- 判断服务端响应是否支持压缩
- net模块
	- 用于创建socket[[服务器]]或者socket客户端
-