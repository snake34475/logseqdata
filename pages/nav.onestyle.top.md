- 收藏各种特色的链接网站
- 网站进度
	- 新增获取nav的展示接口
	- 修改nav
	- 新增nav
		- log上传
		- label
			- 中文
			- 英文
		- link
		- 介绍
	- 删除nav
	- 重组nav(支持子节点更换父节点)
-
- 以下是支持的数据格式
- ```json
  [
    {
      "name": "常用网站", //中文索引
      "en_name": "Tutorial", //英文索引
      "icon": "linecons-pencil",//icon图标
      "children": [
        {
          "name": "日常辅助工具", 
          "en_name": "Design FM",
          "web": [
            {
              "url": "https://chatbot.theb.ai/", //连接url
              "logo": "assets/images/logos/bai.jpg", //图片地址
              "title": "BAI CHAT", //标题
              "desc": "国内免费的chatgpt3.5" //介绍
            }
          ]
        }
  ]
  
  ```