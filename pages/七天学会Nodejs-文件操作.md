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
	- 同步异步异常处理
		- 异步都会返回一个err
			- ```js
			  fs.readFile(pathname,function(err,data){
			  if(err){
			  	}else{
			  }
			  })
			  ```
		- 同步使用try catch异常处理
			- ```js
			  try{
			    var data = fs = readFileSync(pathname);
			  }catch(err){
			    
			  }
			  ```
	- path
		- ```js
		  path.basename()//获取文件名称
		  path.normalize() //格式化路径
		  path.join()//组合多重路径
		  path.extname()//获取路径的后缀
		  ```
	- 遍历目录
		- 遍历一般使用深度优先+先序遍历
			- 查族谱，爷爷>大伯>堂哥>爸爸>我
			- [fs.stat是什么](https://blog.csdn.net/qq_42744920/article/details/123719169)
			- fs.stat获取文件信息，他返回的是文件的实例
				- 1.stats.isFile(): 如果是文件则返回true,否则返回false;
				  2.stats.isDirectiory(): 如果是目录则返回true,否则返回false;
				  3.stats.isBlockDevice(): 如果是块设备则返回true，否则返回false;
				  4.stats.isCharacterDevice(): 如果是字符设备返回true,否则返回false;
				  5.stats.isSymbolicLink(): 如果是软链接返回true,否则返回false;
				  6.stats.isFIFO(): 如果是FIFO,则返回true,否则返回false.FIFO是UNIX中的一种特殊类型的命令管道；
				  7.stats.isSocket(): 如果是Socket则返回true,否则返回false;
				  8.stats.size(): 文件的大小（以字节为单位）。
		- 同步算法
			- ```js
			  function travel(dir,callback){
			      fs.readdirSync(dir).forEach((file)=>{
			          const pathname = path.join(dir,file)
			          if(fs.statSync(pathname).isDirectory()){
			              travel(pathname,callback)
			          }else{
			              callback(pathname,callback)
			          }
			      })
			  }
			  
			  travel("../nodetest",(name)=>console.log(name))
			  ```
	- 文本编码