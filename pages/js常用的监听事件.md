- #js
- > 注意所有的监听事件绑定之后，不用时需要及时清除
- 卸载
	- react
		- ```js
		   return () => {
		              window.removeEventListener('storage', watchingStroage, false);
		          };
		  ```
- 监听缓存更改
	- 介绍：storage事件的介绍[MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/storage_event)
		- 能够实时监听到`localstorage`的变更
			- ```jsx
			   window.addEventListener('storage', watchingStroage, false);
			  ```
	- 使用场景：多屏幕需要实时通讯，通过storage实现
		- 通过判断 变更来源的url中的id与本页面的id是否相同执行操作
		- ```jsx
		    window.addEventListener('storage', watchingStroage, false);
		   	
		        // 监听缓存更改，多页面通信（左、中、右屏）
		      const watchingStroage = e => {
		        //此处为获取来源url中的id
		          const { id } = getUrlParam(e.url);
		        //若id想相同
		          if (id === query?.id) {
		            //并且变更的storage的操作key与预期一致就执行
		              if (e.key === SC_LEFT_SAME) {
		                 console.log(e.newValue)
		              }
		          }
		      };
		  ```
- 监听是否位于前台
	- 支持pc标签，安卓苹果app放到前后台 [MDN文档](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/visibilitychange_event)
	- ```js
	  document.addEventListener("visibilitychange", function() {
	    if (document.visibilityState === "visible") {
	      console.log("标签页变为可见");
	    } else if (document.visibilityState === "hidden") {
	      console.log("标签页变为不可见");
	    }
	  });
	  ```
- 监听resize
- 监听键盘弹出收起
	- ```js
	  /**
	   * 监听键盘，调整dialog的位置
	   * @param keyOut //键盘出来做点什么
	   * @param keyIn //键盘隐藏做点什么
	   * @returns {{name: *, value: *}[]}
	   */
	  export const keyBordCheckDialog=(keyOutFn,keyInFn)=>{
	      var originalHeight = window.innerHeight;
	      window.onresize = function() {
	          var currentHeight = window.innerHeight;
	          if (originalHeight > currentHeight) {
	              // 键盘弹出
	              // console.log("键盘弹出")
	              var popupHeight = originalHeight-currentHeight //窗口偏移量
	              keyOutFn(popupHeight)
	          } else {
	              // 键盘收起
	              // console.log("键盘收起")
	              keyInFn()
	          }
	      };
	  }
	  ```