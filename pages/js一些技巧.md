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