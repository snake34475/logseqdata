- [官方文档](https://cn.vuejs.org/guide/quick-start.html)
- 模板类
	- [v3-admin-vit模块文档](https://juejin.cn/post/7089377403717287972)
- ref
	- 如果子组件使用选项式api，父组件每对子组件的每一个方法和属性都有完全访问权
	- expose限制访问
		- ```js
		   expose: ['publicData', 'publicMethod'],//只能访这些数据或方法
		  ```
- 指令语法
	- https://cn.vuejs.org/assets/directive.69c37117.png
- 响应式
	- 基础
		- vue3中响应式通过proxy实现的
		- vue响应式是对象初始化建立的，不是运行时追踪变化
		- 如果直接修改newObject的值，this.someObject监听不到，但是他的值也会改变，修改someObject时newObject也会改变
		- ```js
		  export default {
		    data() {
		      return {
		        someObject: {}
		      }
		    },
		    mounted() {
		      const newObject = {}
		      this.someObject = newObject
		  
		      console.log(newObject === this.someObject) // false
		    }
		  }
		  ```
	- 声明状态
		- ref
			- ref可以持有任何类型的值，非原始值须使用reactive来转换
			- 模板中使用ref不需要附加value，因为ref会自动解包
			- ```js
			  const count = ref(0)
			  console.log(count.value)//应该从value中拿值
			  
			  <span>{{count}}<span>//不用添加value，会自动解包
			  ```
		- reactive
			- reactive使对象本身具有响应性，访问嵌套对象也会被reactive包裹
				- ```js
				  const proxy = reactive({})
				  
				  const raw = {}
				  proxy.nested = raw
				  //因为此时proxy的nested已经被包裹
				  console.log(proxy.nested === raw) // false
				  ```
			- 缺点
				- 只能用于对象类型，map，set，不能用于原始类型
				- 不能替换对象，因为是通过属性访问实现的，必须保持相同引用
				- 使用解构后响应式失效
				-
		-
- 生命周期函数
	- 其实就在beforecreate多一个setup
	- ```js
	  <script setup>
	  import { onMounted } from 'vue'
	  
	  onMounted(() => {
	    console.log(`the component is now mounted.`)
	  })
	  </script>
	  ```
	- ![lifecycle.16e4c08e.png](../assets/lifecycle.16e4c08e_1699949496642_0.png)
		- https://cn.vuejs.org/assets/lifecycle.16e4c08e.png
-