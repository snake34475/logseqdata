- 模块化
	- 模块初始化
		- 模块化的代码，仅第一次被使用时执行一次，执行后导出对象，之后就被缓存
	- 模块的导入导出
		- ```js
		  //导出
		  let i = 0
		  
		  const counter = () =>{
		      return i ++;
		  }
		  
		  // exports.count = counter 这两个导出方法等价
		  module.exports ={
		      count :counter
		  } 
		  
		  //导入
		  const counter = require("./utils/counter")
		  console.log("Hello World")
		  
		  console.log(counter.count())
		  
		  ```
- 代码的组织和部署
	- 模块路径解析规则
		- require支持斜杠、盘符开头的绝对路径
		- nodejs路径解析规则
			- 内置模块直接声明名称 `require('fs')`
		- node_modules目录
			- 自动去匹配项目内node_modules的包，
			- 或者依次寻找上层目录内的node_modules
			- 可以理解为正常使用npm 下包
		- NODE_PATH 环境变量
			- 允许通过修改环境变量来指定模块搜索路径
			- 可以理解为npm下到global的包
	- 包（package）
		- js模块的基本单位是js文件
		- 多个js模块组成的大模块被称为包
			- 包需要一个入口文件，一般使用index，因为这样可以省略入口文件名称
	- package.json
		- 自定义入口文件名和存放位置，需要一个package.json文件
		- ```json
		  {
		    "name":"cat"
		    "main":"./lib/main.js"
		  }
		  ```
		-
	- 工程目录
		- 命令行程序
			- ```
			  - /home/user/workspace/node-echo/   # 工程目录
			      - bin/                          # 存放命令行相关代码
			          node-echo
			      + doc/                          # 存放文档
			      - lib/                          # 存放API相关代码
			          echo.js
			      - node_modules/                 # 存放三方包
			          + argv/
			      + tests/                        # 存放测试用例
			      package.json                    # 元数据文件
			      README.md                       # 说明文件
			  ```