- 简介
	- nodejs可以管制控制自身的运行环境和状态，也可以创建子进程进行协同，可以多个程序组合在一起共同完成某项工作
- 使用到的工具
	- util https://nodejs.org/docs/latest-v16.x/api/util.html
		- format通常使用于nodejs字符串的拼接，至于为什么使用format而不是使用模板字符串是因为模板字符串容易出现不严谨的类型，而format使用了类似静态的类型，
		- ```js
		  util.format('%s:%s',foo)//
		  ```
- 进程模块
	- process模块 [http://nodejs.org/api/process.html](http://nodejs.org/api/process.html)
		- 他是nodejs的全局对象，用于访问当前nodejs进程和信息
	- child_process模块 [http://nodejs.org/api/child_process.html](http://nodejs.org/api/child_process.html)
		- 它用于nodejs创建和控制子进程，他他提供方法执行外部命令、脚本和可执行文件并进行交互,核心模块是   `.spwn`
	- cluster [http://nodejs.org/api/cluster.html](http://nodejs.org/api/cluster.html)
		- 是child_process 的进一步封装 用于nodejs中实现多进程的模块，可利用多核cpu的优势
-
- 案例
	- 复制文件a到b中
		- bash命令`cp -r source/* target`
		- ```js
		  var child_process = require('child_process')
		  var util = require('util')
		  function copy(source, target,callback){
		      child_process.exec(util.format('cp -r %s/* %s',source,target),callback)
		  }
		  
		  copy('../utils',"../t_utils",function(err){
		      if(err){
		          console.log("复制失败");
		      }else{
		          console.log("复制成功");
		      }
		  })
		  ```
- 常用案例
	- ```js
	  //获取命令行参数
	  process.argv.slice(2) 
	  
	  //退出程序
	  try{
	    
	  }catch{
	    process.exit(1)//可指定退出状态码，如果正常退出状态码为0
	  }
	  ```