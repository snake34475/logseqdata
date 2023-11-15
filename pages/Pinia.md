- 一个拥有组合式api的vue状态管理库，支持服务端渲染
- 优点
	- 热更新
- 高阶用法
	- ```js
	  import { ref, computed } from 'vue'
	  import { defineStore } from 'pinia'
	  
	  export const useCounterStore = defineStore('counter', () => {
	    const count = ref(0)
	    const doubleCount = computed(() => count.value * 2)
	    function increment() {
	      count.value++
	    }
	    return { count, doubleCount, increment }
	  })
	  //调用，这两种方法都可以
	  useCounterStore().count++ 
	  useCounterStore().increment()
	  ```
- 基础定义
	- store
		- 通过defineStore，第一个参数必传且不重复，第二个参数支持setup或options
		- 正常结构
			- ```js
			  export const useCounterStore = defineStore("counter",{
			    state: () => ({count: 0}),
			    getters:{
			      double: (state) => state.count * 2
			    },
			    actions: {
			      increment(){
			        this.count++
			      }
			    }
			  }}
			  ```
		- setup store
			- ref就是state属性
			- computed就是getters
			- function就是action
			- 也可以使用组合式函数，但是这种使用方式会让ssr更复杂
			- ```js
			  import { ref, computed } from 'vue'
			  import { defineStore } from 'pinia'
			  
			  export const useCounterStore = defineStore('counter', () => {
			    const count = ref(0)
			    const doubleCount = computed(() => count.value * 2)
			    function increment() {
			      count.value++
			    }
			    return { count, doubleCount, increment }
			  })
			  
			  ```
		- store是reactive包装，所以不能使用解构，可以使用storeToRefs进行包装结构
			- 方法可以直接解构
			- ```js
			  const store = useCounterStore()
			  //支持结构 state和getter
			  const { name, doubleCount } = storeToRefs(store)
			  // 作为 action 的 increment 可以直接解构，如果从上方解构会报错
			  const { increment } = store 
			  ```
	- state
		- 选项式可以使用$reset重置，组合式不可以 （但需注意，不能从方法中直接结构会报错）
		- 修改
			- 选项式api修改想要直接修改state的值，不能使用mapstate辅助函数，应该使用mapWritable()
			- ```js
			  import { mapWritableState } from 'pinia'
			  import { useCounterStore } from '../stores/counter'
			  
			  export default {
			    computed: {
			      // 可以访问组件中的 this.count，并允许设置它。
			      // this.count++
			      // 与从 store.count 中读取的数据相同
			      ...mapWritableState(useCounterStore, ['count'])
			      // 与上述相同，但将其注册为 this.myOwnName
			      ...mapWritableState(useCounterStore, {
			        myOwnName: 'count',
			      }),
			    },
			  }
			  ```
			- $patch允许修改多个属性,并不会影响到没提及的属性
				- ```js
				  store.$patch({
				    count: store.count + 1,
				    age: 120,
				    name: 'DIO',
				  })
				  //这种方式可以让集合修改更简单
				  store.$patch((state) => {
				    state.items.push({ name: 'shoes', quantity: 1 })
				    state.hasChanged = true
				  })
				  ```
			- 监听
				- subscribe 比watch的优点是patch后只触发一次
		- getter
			- getter不允许传递任何参数，不允许做其他操作
			- getter会被缓存
			- 能够访问其他的store的getter
			-
-