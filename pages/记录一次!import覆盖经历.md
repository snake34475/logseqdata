- #react #antd #less
  id:: 6448f3cb-ed47-4019-82ec-6ffe92748738
- ## 当前的问题
	- 有一全局`global.less`文件控制着全局的样式
		- ![Replaced by Image Uploader](https://s2.loli.net/2023/04/26/kVcrxF8dEhHsPtn.png)
	- 我做了一个范围筛选，里面是两个form嵌套
		- ![Replaced by Image Uploader](https://s2.loli.net/2023/04/26/o7lFwiJNQqcvuIe.png)
	- 由于我是两个formitem嵌套，所以两个margin，导致了高度多一个
		- ![Replaced by Image Uploader](https://s2.loli.net/2023/04/26/RjaQFlTroXCmgqh.png){:height 542, :width 479}
- ## 解决方法
	- 通过先限制一个class，然后在里面写全局，然后再写元素，这样既不影响全局的元素，又能达到目的
		-
		- ![Replaced by Image Uploader](https://s2.loli.net/2023/04/26/tE4yqQdrLM6wZOc.png)
		- 如果将`audit_durationFormItem`直接写在global则不生效
			- ![Replaced by Image Uploader](https://s2.loli.net/2023/04/26/Eu7Jz9NkgKfCb5X.png)
-