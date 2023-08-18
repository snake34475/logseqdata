- 学习 awesome-coding-js
	- js示例
	- [JavaScript专题](https://www.conardli.top/docs/JavaScript/)
	- DONE [手动实现call、apply、bind](https://www.conardli.top/docs/JavaScript/%E6%89%8B%E5%8A%A8%E5%AE%9E%E7%8E%B0call%E3%80%81apply%E3%80%81bind.html)
	  collapsed:: true
		- 都是用来改变[this指向](https://zhuanlan.zhihu.com/p/42145138)，说到this指向，this只会指向调用他的对象
		  this中的两个要点，1一定会指向一个对象，2指向调用他的
		- call和apply和bind第一个参数都是对象，如果不传那就是window
		  call和bind第二以及之后都是传递的参数，apply第二个参数是一个数组
			- 注意！虽然apply和bind第二个参数传递的类型不一样，但是在实际的参数调用时，传给函数的都是python中的元组类的也就是和call一样一个一个传递的，而不是数组
		- call和apply是立即执行的，而bind是先绑定到一个函数上，之后才去执行
		- 函数的实现
			- 原理：call和apply将函数赋值给要指向的对象，调用后删除这个属性
			  bind是将函数赋值给要指向的对象，创建一个闭包，根据是否为构造函数判断new一个函数还是使用apply调用
		- 扩展
			- arguments和args，arguments是类数组对象，而args是纯数组
	- LATER [EventEmitter](https://www.conardli.top/docs/JavaScript/EventEmitter.html)
	- DONE [防抖](https://www.conardli.top/docs/JavaScript/%E9%98%B2%E6%8A%96.html)
	  collapsed:: true
		- 防止单位时间内多次点击，我们希望在单位时间内若有重复点击，将其他点击取消，只执行一次，因此在你限定的时间内他只会执行最后一次
			- ```javascript
			  //我们根据关键词，既然和时间相关，那么一定会使用到settimeout或者setinterval
			  //将之前的次数取消，那么肯定会将声明的settimeout赋值于一个变量，并且使用了clearTime进行清空
			  //又因为需要再函数内存储公共变量，此时就可以想到闭包
			  function debounce(event,time){
			    let timer=null;
			    //此处为接受所有的参数为一个args数组，此后可以使用...args数组进行取值操作
			    return function(...args){
			      //clearTImeout为清楚定时器，清楚后直接回收，不会存在内存中
			      clearTimeout(timer)
			      timer=setTimeout(()=>{
			        //使用apply是因为apply参数能接受一个数组
			        event.apply(event,args)
			      },time)
			    }
			  }
			  ```
	- DONE [节流](https://www.conardli.top/docs/JavaScript/%E8%8A%82%E6%B5%81.html)
	  collapsed:: true
		- 我们希望防止单位内多次点击，但是我们又希望不全部取消，可以积攒一段时间再去取消，所以节流就出现了
			- ```
			  ```
	- LATER [浅拷贝和深拷贝](https://www.conardli.top/docs/JavaScript/%E6%B5%85%E6%8B%B7%E8%B4%9D%E5%92%8C%E6%B7%B1%E6%8B%B7%E8%B4%9D.html)
	- DONE [数组去重、扁平、最值](https://www.conardli.top/docs/JavaScript/%E6%95%B0%E7%BB%84%E5%8E%BB%E9%87%8D%E3%80%81%E6%89%81%E5%B9%B3%E3%80%81%E6%9C%80%E5%80%BC.html)
	- DONE [数组乱序-洗牌算法](https://www.conardli.top/docs/JavaScript/%E6%95%B0%E7%BB%84%E4%B9%B1%E5%BA%8F-%E6%B4%97%E7%89%8C%E7%AE%97%E6%B3%95.html)
		- 其实用了一个随机函数，遍历所有的当前项和随机项进行替换，从而实现了洗牌
	- DONE [函数柯里化](https://www.conardli.top/docs/JavaScript/%E5%87%BD%E6%95%B0%E6%9F%AF%E9%87%8C%E5%8C%96.html)
		- 多个参数的函数，改成多次传一个参数的函数，利于参数的封装，如果参数传递不够，就等着等下次参数够了再调用执行，这样参数也不会内置到函数中，比较灵活
	- LATER [手动实现JSONP](https://www.conardli.top/docs/JavaScript/%E6%89%8B%E5%8A%A8%E5%AE%9E%E7%8E%B0JSONP.html)
		- 1.了解什么是jsonp
		- 2.jsonp的原理
	- LATER [模拟实现promise](https://www.conardli.top/docs/JavaScript/%E6%A8%A1%E6%8B%9F%E5%AE%9E%E7%8E%B0promise.html)
	- LATER [手动实现ES5继承](https://www.conardli.top/docs/JavaScript/%E6%89%8B%E5%8A%A8%E5%AE%9E%E7%8E%B0ES5%E7%BB%A7%E6%89%BF.html)
	- DONE [手动实现instanceof](https://www.conardli.top/docs/JavaScript/%E6%89%8B%E5%8A%A8%E5%AE%9E%E7%8E%B0instanceof.html)
	- LATER [基于Promise的ajax封装](https://www.conardli.top/docs/JavaScript/%E5%9F%BA%E4%BA%8EPromise%E7%9A%84ajax%E5%B0%81%E8%A3%85.html)
	- DONE [单例模式](https://www.conardli.top/docs/JavaScript/%E5%8D%95%E4%BE%8B%E6%A8%A1%E5%BC%8F.html)
	- DONE [异步循环打印](https://www.conardli.top/docs/JavaScript/%E5%BC%82%E6%AD%A5%E5%BE%AA%E7%8E%AF%E6%89%93%E5%8D%B0.html)
	- DONE [图片懒加载](https://www.conardli.top/docs/JavaScript/%E5%9B%BE%E7%89%87%E6%87%92%E5%8A%A0%E8%BD%BD.html)
	-