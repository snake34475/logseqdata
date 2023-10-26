-
- post
	- body
		- `application/x-www-form-urlencoded`
		  最常见的post提交，相当于原生form提交
		  ```http
		  POST http://www.example.com HTTP/1.1
		  Content-Type: application/x-www-form-urlencoded;charset=utf-8
		  
		  title=ahweg&sub%5B%5D=1&sub%5B%5D=2&sub%5B%5D=3
		  ```
		- `multipart/form-data`
		  上传文件，或者表单数据
		  他生成了一个boundary的字段，然后消息主体的每部分都是boundary开始，内容，最后主体以boundary结束
		  ```http
		  POST http://www.example.com HTTP/1.1
		  Content-Type:multipart/form-data; boundary=----WebKitFormBoundaryrGKCBY7qhFd3TrwA
		  
		  ------WebKitFormBoundaryrGKCBY7qhFd3TrwA
		  Content-Disposition: form-data; name="ahweg"
		  
		  title
		  ------WebKitFormBoundaryrGKCBY7qhFd3TrwA
		  Content-Disposition: form-data; name="file"; filename="ahweg.png"
		  Content-Type: image/png
		  
		  PNG ... content of ahweg.png ...
		  ------WebKitFormBoundaryrGKCBY7qhFd3TrwA--
		  ```
		- `text/xml`
		  ```http
		  POST http://www.example.com HTTP/1.1 
		  Content-Type: text/xml
		  
		  <?xml version="1.0"?>
		  <methodCall>
		      <methodName>examples.getStateName</methodName>
		      <params>
		          <param>
		              <value><i4>125</i4></value>
		          </param>
		      </params>
		  </methodCall>
		  ```
- 常见http请求问题
	- fetch请求的数据如何发送类似formdata的请求
	  ![Replaced by Image Uploader](https://s2.loli.net/2023/10/25/l5MJh7sLinR4tmf.png)
	  https://s2.loli.net/2023/10/25/l5MJh7sLinR4tmf.png
		- 背景：正常axios发送的请求就是这种formdata的格式，但是因为需求中需要用到关闭页面前发送一次请求，发现fetch的keepalive可以实现这个需求，在封装fetch的时候发现之前项目中传参是json，希望使用formdata进行传参，但是直接声明content-type发现传参不生效
		- 解决方案：
		  * headers头中不添加Content-Type:multipart/form-data
		  * body内使用new formdata进行实现
		- 代码如下
		  ![Replaced by Image Uploader](https://s2.loli.net/2023/10/25/3R6yxB7pfzLQ8Ui.png)
		- [引用1 fetch发送formdata格式发送数据带json格式](https://blog.csdn.net/Akukudeteng/article/details/120909748)
	-