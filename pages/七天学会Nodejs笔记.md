- nodejs其实是js脚本解析器
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
- 文件操作
	- 写入到一个新的文件
		- >由于argv[0]固定等于NodeJS执行程序的绝对路径，argv[1]固定等于主模块的绝对路径，因此第一个命令行参数从argv[2]这个位置开始。
		- ```js
		  var  fs = require("fs")
		  
		  //直接复制小文件，可能爆仓
		  function copy (src,dst){
		      fs.writeFileSync(dst,fs.readFileSync(src))
		  }
		  //复制大文件，不会爆仓
		  function copyBig(src,dst){
		      fs.createReadStream(src).pipe(fs.createWriteStream(dst))
		    //先创建一个只读数据流，然后创建一个只写数据流，然后使用pipe连接起来
		  }
		  
		  function main (argv){
		      copy(argv[0],argv[1])
		  }
		  
		  console.log("arg",process.argv)
		  
		  /* argv 
		  argv [
		    'D:\\install\\nvm\\nodejs\\node.exe',
		    'D:\\codetest\\nodejs\\nodetest\\main.js',
		    'D:/codetest/nodejs/nodetest/main.js',
		    'D:/codetest/nodejs/nodetest/utils/main.js'
		  ] */
		  main(process.argv.slice(2));
		  
		  //node main.js /d/codetest/nodejs/nodetest/main.js /d/codetest/nodejs/nodetest/utils/main.js
		  ```
	- 部分api
		- Buffer数据块
			- 可以通过读取文件获取Buffer实例，还能直接构造
			- ```js
			  var bin = new Buffer([ 0x68, 0x65, 0x6c, 0x6c 0x6f])
			  //下标获取
			  bin[0] = 0x68l
			  var str = bin.toString('utf-8') //hello
			  var bin = new Buffer("hello",'utf-8') //构造出来一个buff
			  ```
			- buffer可以视为一个数组，对他的修改都会影响之前的
			- ```js
			  var bin = new Buffer([ 0x68, 0x65, 0x6c, 0x6c 0x6f])
			  var dup = new Buffer(bin.length)
			  
			  bin.copy(dup)
			  dup[0] = 0x48
			  console.log(bin); // => <Buffer 68 65 6c 6c 6f>
			  console.log(dup); // => <Buffer 48 65 65 6c 6f>
			  ```
	- fs文件[[系统]]
		- 文件属性读写
			- ```js
			  fs.stat fa.chmod fs.chown
			  ```
		- 文件内容读写
			- ```js
			  fs.readFile fs.reddir fs.writeFile fs.mkdir
			  ```
		- 底层文件操作
			- ```js
			  fs.open fs.read fs.write fs.close
			  ```
-