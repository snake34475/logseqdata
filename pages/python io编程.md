## IO编程
	- ###  文件读写
	  collapsed:: true
		- ```python
		  #r表示读
		  f = open('/Users/michael/test.txt', 'r')
		  #读到内存中
		  f.read()
		  #隔壁文件，因为会占用操作系统资源
		  f.close()
		  
		  #二进制文件，图片，视频等等
		  >>> f = open('/Users/michael/test.jpg', 'rb')
		  ```
		- 通常写法，python自己调用close关闭
			- ```python
			  with open('/path/to/file', 'r') as f:
			      print(f.read())
			      
			  #w 没有就新建， a的话是追加
			  with open('/Users/michael/test.txt', 'w') as f:
			      f.write('Hello, world!')
			  ```
		- 注意
			- ```python
			  #r表示读
			  f = open('/Users/michael/test.txt', 'r')
			  
			  
			  #读到内存中
			  f.read()
			  #隔壁文件，因为会占用操作系统资源
			  f.close()
			  ```
	- ### 缓存
		- #### StingIO
			- ```python
			  ## 写入
			  form io import StringIO
			  f=StringIO()
			  f.write("hellow")
			  print(f.getvalue())
			  
			  #读取
			  form io import StringIO
			  f=StringIO('Hello!\nHi!\nGoodbye!')
			  while True:
			    s=f.readline()
			    if s=='':
			      break
			    print(s.strip())
			  ```
		- #### BytesIO
			- ```python
			  form io import BytesIO
			  f=BytesIO()
			  f.write("中文".encode("utf-8"))
			  print(f.getvalue())
			  
			  >>> from io import BytesIO
			  >>> f = BytesIO(b'\xe4\xb8\xad\xe6\x96\x87')
			  >>> f.read()
			  ```
	- ### 操作文件目录
		- ```python
		  >>> import os
		  >>> os.name # 操作系统类型
		  >>> os.environ #环境变量
		  >>> os.environ.get('PATH') #获取某个特定的值
		  
		  
		  # 查看当前目录的绝对路径:
		  >>> os.path.abspath('.')
		  '/Users/michael'
		  # 在某个目录下创建一个新目录，首先把新目录的完整路径表示出来:
		  >>> os.path.join('/Users/michael', 'testdir')
		  '/Users/michael/testdir'
		  # 然后创建一个目录:
		  >>> os.mkdir('/Users/michael/testdir')
		  # 删掉一个目录:
		  >>> os.rmdir('/Users/michael/testdir')
		  #拆分路径
		  >>> os.path.split('/Users/michael/testdir/file.txt')
		  ('/Users/michael/testdir', 'file.txt')
		  #os.path.splitext()可以直接让你得到文件扩展名
		  >>> os.path.splitext('/path/to/file.txt')
		  ('/path/to/file', '.txt')
		  
		  ##列出所当前目录下所有文件
		  >>> [x for x in os.listdir('.') if os.path.isdir(x)]
		  #要列出所有的.py文件
		   [x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1]=='.py']
		  ```
		-
- ## 进程和线程
	- 多任务
		- > 就是能够一边听歌，看电视剧，赶作业
		- 多任务有以下三种方法可以实现
			- 多进程
				- fork
					- Unix提供一个fork调用，他调用一次返回两次，因为把当前进程(父进程)复制一份(子进程),然后分别在父和子返回，子进程返回0，父进程返回子进程的id
					- 这样一个进程在接到新任务的时候就可以复制出来一个子进程来处理新任务，例如常见的Apache[[服务器]]
					- getpid 获取当前进程的pid，进程标识号
					- getppid 获取当前进程的父进程pid
				- mulitiprocessing
					- window没有fork调用，一般只有Unix/Linux有，multiprocessing就是跨平台多版本的多进程模块
					-
			- 多线程
			- 多进程+多线程
		- 单核多任务
			- 1任务执行0.01s，2任务执行0.01s然后交替执行，因为执行快所有以为是同时执行
	- 进程(process)
		- > 打开浏览器就是进程，启动记事本就是进程，word也是进程
		- 线程(Thread)
			- 可以在进程中同时干的事情，例如wps的打字，拼写检查等等，每个人任务的子任务被称为线程
			- [[$red]]==一个进程至少要有一个线程==
		-
	-
- ## 异步IO
	- ## 协程
		- >是指一种轻量的线程，可以在同一个线程中交替执行，避免线程切换的开销
		- 子程序调用只是一个入口一个返回，而携程可以内部中断，进而执行其他程序
		- ### 优点
			- 执行效率高，不需要像子程序一样创建和销毁函数栈
			- 可以在同一个线程交替执行，避免切换线程
			- 灵活，可以暂停等待某个时间，方便实现异步
		- 使用
			- 通过generator实现
		- 方法
			- next
				- 执行
		-
	- ## asyncIO
		- ```python
		  import asyncio
		  
		  @asyncio.coroutine
		  def hello():
		      print("Hello world!")
		      # 异步调用asyncio.sleep(1):
		      r = yield from asyncio.sleep(1)
		      print("Hello again!")
		  
		  #老方法
		  # 获取EventLoop:
		  loop = asyncio.get_event_loop()
		  # 执行coroutine
		  loop.run_until_complete(hello())
		  loop.close()
		  
		  #新方法 3.7以上，不用自动关闭
		  asyncio.run(hello())
		  ```
	- aiohttp
		- 基础案例
		- ```python
		  import asyncio
		  from aiohttp import web
		  
		  async def index(request):
		      await asyncio.sleep(0.5)
		      return web.Response(text='<h1>index</h1>',content_type='text/html')
		  
		  async def hello(request):
		      await asyncio.sleep(0.5)
		      name=request.match_info['name']
		      text=f'<h1>hello ,{name}</h1>'
		      return web.Response(text=text,content_type='text/html')
		  
		  async def init_app():
		      app=web.Application()
		      app.add_routes([
		          web.get('/',index),
		          web.get('/hello/{name}',hello)
		      ])
		      return app
		  
		  app=asyncio.run(init_app())
		  print('Server stared at http://127.0.0.1:8000')
		  web.run_app(app,host='127.0.0.1',port=8000)
		  ```