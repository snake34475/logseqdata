- #宝塔面板 #redis
- ## 准备
	- 宝塔面板
	- [resp](https://pan.baidu.com/s/1mezyPkU6Rtp0mSkKredYuw?pwd=9dgs) 
	  redis远程连接软件
-
-
- id:: 6447b644-be51-4cd4-9c5e-cabead43ee47
  1. 软件商店查询redis 点击设置
  ![Replaced by Image Uploader](https://s2.loli.net/2023/04/25/23SwGaXlWnDhJsr.png){:height 290, :width 539}
- 2.修改这两项
	- bind
	- requirepass
	- ![Replaced by Image Uploader](https://s2.loli.net/2023/04/25/zLeh1VJnlTA8wkx.png){:height 415, :width 509}
- 3.重启
- 4.端口号开放6379
	- 宝塔端口开启
		- 如果看到这个防火墙开关开启的话，记得把端口放行一下
		  ![Replaced by Image Uploader](https://s2.loli.net/2023/04/25/OGfRisW8TnIzF94.png)
	- 腾讯/阿里云控制台防火墙开启，一般在服务器的页面
		- ![Replaced by Image Uploader](https://s2.loli.net/2023/04/25/NpMrO58nPbTocAI.png)
- 5