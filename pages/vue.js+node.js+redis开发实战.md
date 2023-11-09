- [微信读书](https://weread.qq.com/web/reader/c7432440721c7eb2c74881fk7e7327a02a67e7757b1e50a)
-
- 项目初始准备
	- express脚手架
	- 启动redis
	- redis[[服务器]]配置
	- redisDB封装方法
	- middleware添加中间件校验
	- 路由与逻辑解耦
- 难点
	- redisDB中
		- scan与有序集合
	- 热点文章的新增和获取
		- 修改
			- 找id存在直接替换
		- 新增
			- 获取自增id，根据自增id插入文章
			- 获取类型，进行类型的插入
			- 获取tags的类型，进行tags的插入
		- 获取
			- 根据浏览量正序取5条
	- 困难的接口
		- 其他权限判断
- ```js
  //取出 排序的范围值
  redis.zrevrange(key, 0, 4).then(async (data) => {})
  //写入 分值
   redis.zadd(fapp + ':a_like', key, 0)
  //获取分值的值
  redis.zscore(fapp + ':a_view', key).then(view => {}）
  ```
- 经常遇到的问题
	- Cannot set headers after they are sent to the client
		-
-