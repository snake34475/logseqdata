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