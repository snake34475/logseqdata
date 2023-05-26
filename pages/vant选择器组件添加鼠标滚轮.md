- 平常做[[前端]]开发的应该知道，在[[前端]]组件中，有两种组件
	- 一种是针对移动端的组件
	- 另一种是针对pc的组件
- 而pc的组件主要是对鼠标，键盘等操作的支持，而移动端组件常用的事件是触摸等事件
- 这时，狗血的就来了，业务总是能用各种奇怪的[[想法]]让你来回串着走
          我们有一款web是写在企业微信内部的h5网页，他使用的是移动端组件，但是这个应用由于企业微信手机端和电脑端都有，导致了业务也会用电脑操作的需求
          这天，他说选项组件为什么不能使用滚轮选择？而是只能使用拖拽？这样
-
- [github原回答是不支持的](https://github.com/youzan/vant/issues/4617)
- [csdn](https://blog.csdn.net/lllomh/article/details/118891814?ops_request_misc=&request_id=&biz_id=102&utm_term=vant%20picker%E7%BB%84%E4%BB%B6%E5%9C%A8pc%E9%BC%A0%E6%A0%87%E6%BB%9A%E8%BD%AE&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-118891814.nonecase&spm=1018.2226.3001.4187)解决方案，改源码，有点麻烦
- hammerjs 添加模拟事件