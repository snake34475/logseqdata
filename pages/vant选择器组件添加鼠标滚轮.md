- 平常做[[前端]]开发的应该知道，在[[前端]]组件中，有两种组件
	- 一种是针对移动端的组件
	- 另一种是针对pc的组件
- 而pc的组件主要是对鼠标，键盘等操作的支持，而移动端组件常用的事件是触摸等事件
- 这时，狗血的就来了，业务总是能用各种奇怪的[[想法]]让你来回串着走
          我们有一款web是写在企业微信内部的h5网页，他使用的是移动端组件，但是这个应用由于企业微信手机端和[[电脑]]端都有，导致了业务也会用[[电脑]]操作的需求
          这天，他说选项组件为什么不能使用滚轮选择？而是只能使用拖拽？这样不好用，要改成也支持滚轮
          首先咱们就去看这个组件，也就是 [vant官方库](https://vant-contrib.gitee.io/vant/#/zh-CN/home),他有一个能够兼容桌面的
   ![Replaced by Image Uploader](https://s2.loli.net/2023/05/26/TkeGrNVwLdtYpbf.png)
          这咱们一看就来劲儿了呀
- 这时，狗血的就来了，业务总是能用各种奇怪的想法让你来回串着开发
  
  ​        我们有一款web是写在企业微信内部的h5网页，他使用的是移动端组件，但是这个应用由于企业微信手机端和电脑端都有，导致了业务也会用电脑操作的需求
  
  ​        这天，他说选项组件为什么不能使用滚轮选择？而是只能使用拖拽？这样不好用，要改成也支持滚轮
## 解决路径

>  嫌麻烦，请直接跳到最后的解决方案，前面只是解决路程
- ### vant组件库
  
  ​        首先咱们就去看这个组件，也就是 [vant官方库](https://vant-contrib.gitee.io/vant/#/zh-CN/home),他有一个能够兼容桌面的
   ![Replaced by Image Uploader](https://s2.loli.net/2023/05/26/TkeGrNVwLdtYpbf.png)
  ​        这咱们一看就来劲儿了呀，正好咱们要用鼠标滚轮，肯定能够实现鼠标滚轮模拟拖拽呀，咱们继续往下看下去
  
  ![image-20230526095415573](https://s2.loli.net/2023/05/26/MbRjfFO9e7aKAnV.png)[[2023年05月26日]]
  
  ​		然后发现本地项目中已经安了这个插件，但是滚轮效果仍然不生效，于是乎，这种方法不可以
### gihtub issues

​		当然，如果咱们只会查文档解决问题那么咱们就不是合格的程序员了，咱们也要学会去源码项目的issues，于是咱们去看下[vant项目源码](https://github.com/youzan/vant)

​		看到关于滚轮的有19个已解决，咱们就开心了，看来前人已经把路子探好了，咱们直接copy就行了

![image-20230526095841938](https://s2.loli.net/2023/05/26/PAY8jVxviECzhKa.png)

​		然后看到开发大大的回答就哭了，没计划支持，以后也不会支持，

![image-20230526100016718](https://s2.loli.net/2023/05/26/pFEGXyaz97esIR3.png)
### CSDN

​		[csdn回答]([csdn](https://blog.csdn.net/lllomh/article/details/118891814?ops_request_misc=&request_id=&biz_id=102&utm_term=vant%20picker%E7%BB%84%E4%BB%B6%E5%9C%A8pc%E9%BC%A0%E6%A0%87%E6%BB%9A%E8%BD%AE&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-118891814.nonecase&spm=1018.2226.3001.4187)解决方案，改源码，有点麻烦) 这种方法也时候也能解决一些问题，但是他通过改node_modules解决的，这种方法涉及到如何把源码包抽离出来，进行更改，然后所有的引入源也更改，比较麻烦，而且害怕涉及到线上问题
### hammerjs

​		再后来就想着使用hammerjs模拟手指操作可以么？滚轮滚一个，然后模拟手指滑动多少距离，这样就不用麻烦判断边界问题和选中问题，但是通过引入hammerjs问题频频。例如获取dom的麻烦等等问题，并且无法监听你是否能够监听你是否模拟成功了，所以这种也不行
- ### 换组件！！
  
  ​		换组件的话意味着重写，开发周期起码两天以上，这种特别麻烦
  
  ​		我尝试使用
	- Mint UI
	- Cube UI
	- Vux
	- MUI
	  
	  等等，但是都没发现，突然我想看看antd-mobile，哭了，发现他有，但是他是react组件，vue和react串着写，肯定不可能呀
	  
	  ![image-20230526101205773](https://s2.loli.net/2023/05/26/jL4n6XUElsDQfWV.png)
### chatGPT(最终解决方案)
	- #### 改组件
	  
	  ​		其实上面换组件，和使用hammerjs都是他给我推荐的，可能是关键词不行？后来一个解决方法不用换组件，可以在原生写
	  
	  原回答如下
	  
	  1. 在 `mounted` 钩子函数中，获取到 Picker 组件的 DOM 元素，并添加 `wheel` 事件监听函数。
	  
	  2. 在 `wheel` 事件监听函数中，根据鼠标滚轮滚动的方向来修改 Picker 组件的选中值。可以通过调用 `scrollToOption` 方法来实现滚动选中值的效果。
	  
	  ```vue
	  <template>
	  <div>
	    <van-picker
	      ref="picker"
	      :columns="columns"
	      @change="handleChange"
	      :default-index="currentIndex"
	    />
	  </div>
	  
	  </template>
	  
	  <script>
	   // 如果不是v2记得把 :default-index="currentIndex"属性删掉，虽然我也不知道会出现什么错误
	  import { Picker } from 'vant';
	  
	  export default {
	  components: {
	    [VanPicker.name]: Picker,
	  },
	  data() {
	    return {
	      columns: ['A', 'B', 'C', 'D', 'E'],
	      currentIndex: 0
	    };
	  },
	  mounted() {
	    //获取到picker的dom
	    //如果咱们在pouop里面写的话，就应该写到当弹窗出来再获取dom，否则获取不出来
	    const pickerEl = this.$refs.picker.$el;
	    pickerEl.addEventListener('wheel', this.handleWheel);
	  },
	  methods: {
	    handleChange(value, index) {
	      this.currentIndex = index;
	      console.log('Selected value(value, index)', value, index);
	    },
	    handleWheel(event) {
	      event.preventDefault();
	      //Math.sign()函数，返回+/-1，表示正数还是负数，例如deltaY发现是-100，那么Math.sign返回也是-1，但是传入0那就是0
	      const delta = Math.sign(event.deltaY);
	      //获取最大下标
	      const maxIndex = this.columns.length - 1;
	      //计算当前下标，因为滚轮和拖拽是相反的逻辑，我们可以试下，触控板和鼠标滚轮就是相反的，所以要减
	      const newIndex = this.currentIndex - delta;
	      //边界处理
	      if (newIndex >= 0 && newIndex <= maxIndex) {
	        this.currentIndex = newIndex;
	        //动画可能不流畅
	        //vant 4的话
	        this.$refs.picker.scrollToOption(newIndex);
	        //vant3  this.$refs.picker.scrollToOption(newIndex);
	        //vant2 的解决方案，我是以下的解决方法解决的
	          //这个是控制动画的时长
	         //  this.$refs.picker.$el.getElementsByClassName('van-picker-column__wrapper')[0].style.transitionDuration='800ms'
	        //这个是给哪个变化添加属性，由于省事就添加all
	      //this.$refs.picker.$el.getElementsByClassName('van-picker-column__wrapper')[0].style.transitionProperty='all'
	      }
	    }
	  },
	  };
	  </script>
	  ```
	  
	  ​		在这个示例中，我们在 `mounted` 钩子函数中获取到了 Picker 组件的 DOM 元素，并添加了 `wheel` 事件监听函数。在 `handleWheel` 方法中，我们根据鼠标滚轮滚动的方向来修改 Picker 组件的选中值，并调用 `scrollToOption` 方法来实现滚动选中值的效果。最后，我们在 `handleChange` 方法中输出了选中的值和索引。
	  
	  需要注意的是，在 `handleWheel` 方法中，我们调用了 `event.preventDefault()` 来阻止浏览器默认的滚动行为，以避免与 Picker 组件的滚动效果冲突。
#### 如何全局生效？

使用混入，以下是全部代码，我的vant是2版本

```js
// mixins.js 文件
//1.picker组件需要添加ref
//2.骗
export const myMixin = {
  methods: {
      //这个事件放到picker弹出的地方
      /***
       * picker滚动事件
       * @param picker picker的ref
       * @param cloum picker的数据
       * @param getCurFn 默认选中的index,是一个函数，因为需要拿到实时的
       * @param setIndex 设置index的方法
       * @returns {Promise<void>}
       */
      async getpicker(picker,cloum,getCurFn,setIndex){

          await new Promise(resolve => {setTimeout(resolve,100)})
          const pickerEl = this.$refs[picker].$el;
          pickerEl.addEventListener('wheel', (event)=>this.handleWheel(event,picker,cloum,getCurFn,setIndex));
          // console.log("pickerEl",pickerEl)
      },
      handleWheel(event,picker,cloum,getCurFn,setIndex) {
          // debugger
          event.preventDefault();
          const delta = Math.sign(event.deltaY);
          // debugger
          const maxIndex = cloum.length - 1;
          const newIndex = getCurFn() + delta;
          // debugger
          this.$refs[picker].$el.getElementsByClassName('van-picker-column__wrapper')[0].style.transitionDuration='800ms'
          this.$refs[picker].$el.getElementsByClassName('van-picker-column__wrapper')[0].style.transitionProperty='all'
          if (newIndex >= 0 && newIndex <= maxIndex) {
              // this.popupData.defaultIndex = newIndex;
              // console.log(" setIndex", setIndex,newIndex)
              setIndex(newIndex)
          }
      },
  }
};

```

调用

```js
 this.getpicker('picker',this.popupData.comSurList,()=>this.popupData.defaultIndex,(index)=>this.popupData.defaultIndex=index)
```
-
- [github原回答是不支持的](https://github.com/youzan/vant/issues/4617)
- [csdn](https://blog.csdn.net/lllomh/article/details/118891814?ops_request_misc=&request_id=&biz_id=102&utm_term=vant%20picker%E7%BB%84%E4%BB%B6%E5%9C%A8pc%E9%BC%A0%E6%A0%87%E6%BB%9A%E8%BD%AE&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-118891814.nonecase&spm=1018.2226.3001.4187)解决方案，改源码，有点麻烦
- hammerjs 添加模拟事件