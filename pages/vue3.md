- [官方文档](https://cn.vuejs.org/guide/quick-start.html)
- 模板类
	- [v3-admin-vit模块文档](https://juejin.cn/post/7089377403717287972)
- 组件库
	- [antdv](https://www.antdv.com/components/overview)
	- [element-plus](https://element-plus.org/zh-CN/)
	-
- 关键词
	- SFC（Single-File Componen）单文件组件
	- RFC（request for comments）[请看介绍](https://github.com/vuejs/rfcs)
		- 简单来说文件通过讨论，审查，修改，改进，达成共识之后进入实时
- ref
	- 如果子组件使用选项式api，父组件每对子组件的每一个方法和属性都有完全访问权
	- expose限制访问
		- ```js
		   expose: ['publicData', 'publicMethod'],//只能访这些数据或方法
		  ```
- 组合式函数
	- 封装组件
		- 可以看到，和react几乎一样，只是ref可以认为是usestate
		- ```js
		  //组件方法
		  // mouse.js
		  import { ref, onMounted, onUnmounted } from 'vue'
		  
		  // 按照惯例，组合式函数名以“use”开头
		  export function useMouse() {
		    // 被组合式函数封装和管理的状态
		    const x = ref(0)
		    const y = ref(0)
		  
		    // 组合式函数可以随时更改其状态。
		    function update(event) {
		      x.value = event.pageX
		      y.value = event.pageY
		    }
		  
		    // 一个组合式函数也可以挂靠在所属组件的生命周期上
		    // 来启动和卸载副作用
		    onMounted(() => window.addEventListener('mousemove', update))
		    onUnmounted(() => window.removeEventListener('mousemove', update))
		  
		    // 通过返回值暴露所管理的状态
		    return { x, y }
		  }
		  
		  //  在组件中使用
		  <script setup>
		  import { useMouse } from './mouse.js'
		  
		  const { x, y } = useMouse()
		  </script>
		  
		  <template>Mouse position is at: {{ x }}, {{ y }}</template>
		  ```
	- 异步请求
		- 接收响应式状态
		- toValue
			- 3.3新增，将ref或getter规范成值，ref和函数都会成值，否则返回输入
	- 命名
		- 通常使用use开头的驼峰
		-
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