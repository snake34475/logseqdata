- 按钮添加绝对定位，导致按钮无法点击，通过添加z-index解决问题
- 常用的选择器样式写法
	- ```css
	  .new_car_reference_btn_skip{
	        background-color: #6e6e6e;
	        color: white;
	        border: #6e6e6e;
	        &:hover,&:focus{
	          width: 35%;
	          background-color: #6e6e6e;
	          color: white;
	          border: #6e6e6e;
	        }
	      }
	  ```
- 修复100vh bug [文章链接](https://juejin.cn/post/7313979304513552435)
	- 地址栏可能会导致100vh比本来更长
	- ```js
	  //第一种方案    
	  //初始状态box的高度
	      let height = window.innerHeight 
	      document.querySelector('.box').style.setProperty("--vh",`${height}px`)
	  
	  
	      //变化时box的高度
	      window.addEventListener("resize",function(e){
	          let height = window.innerHeight
	          document.querySelector(".box").style.setProperty("--vh",`${height}px`)
	      })
	  //css
	          .box {
	              background-color: wheat;
	              height: 100vh;
	              height:var(--vh);
	          }
	  
	  //第二种方案
	      .box {
	              background-color: wheat;
	              height: 100dvh; //新出属性，始终会占满，但是可能会有兼容性
	          }
	  ```
- 企业微信margin高度bug
	- 企业微信设计margin的时候，可能会有重复margin的情况，解决方法是给父级添加overflow，其他浏览器目前没有发现这个问题
	-