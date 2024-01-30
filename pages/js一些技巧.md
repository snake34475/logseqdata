-
- ## 写css
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
	- ```js
	  //控制台 使用%c为css占位符
	  console.log('%cHello %cWorld', 
	  'color: red; font-weight: bold',  
	  'color: blue; font-style: italic');
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
- 数组自定义排
	- ```js
	  const _ = require('lodash');
	  
	  const cities = [
	    { city: '上海', population: 24150000 },
	    { city: '北京', population: 21710000 },
	    { city: '河南', population: 96000000 },
	    { city: '广州', population: 14000000 },
	  ];
	  
	  const cityOrder = ['北京', '上海', '河南'];
	  
	  // 使用Lodash的sortBy函数进行排序
	  const sortedCities = _.sortBy(cities, (city) => {
	    return _.indexOf(cityOrder, city.city);
	  });
	  ```