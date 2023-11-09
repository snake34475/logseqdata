## 写css
	- ```js
	  // 这种写css的方法多优雅
	  canvas.style.cssText = [
	        "display: block",
	        "position: absolute",
	        "top: 0",
	        "left: 0",
	        "pointer-events: none",
	      ].join(";");
	  ```
- 判断对象内有值
	- ```js
	  //判断obj中是否有相应的key
	  if("abc" in obj){
	  ....
	  }
	  ```
- 判断浏览器前缀
	- ```js
	  ```
- 判断是不是[[服务器]]
	- ```js
	  const isServer = typeof window === 'undefined'
	  ```