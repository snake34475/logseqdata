- window安装sonaar
  
  > 最好使用docker装，因为需要java特定环境，
## docker安装方法
- ### 安装sonarqube
	- [官网教学](https://docs.sonarqube.org/latest/try-out-sonarqube/) 
	  
	  > 因为官网某些地方没有成功运行，以下是成功运行的步骤
		- 1.首先本地有docker，docker配置下阿里云镜像
		  
		  	[阿里云镜像配置指南](https://help.aliyun.com/document_detail/60750.html)
		- 2.拉取镜像
		  
		  ```
		  $ docker pull sonarqube
		  ```
		- 3.运行镜像,官网那种方法我没有看懂，我使用了可视化运行
		  
		  ![image-20230113140106316](https://s2.loli.net/2023/01/13/lpDfZYbFLP9iSn8.png)
		- 4.打开[http://localhost:9000/](http://localhost:9000/)，进行登录,初始密码和账号都为admin
		- 5.安装中文，第一次进入插件上方有一个提示点击后才能安装
		  
		  ![image-20230113140319493](https://s2.loli.net/2023/01/13/EmRhFQAypq8YIG2.png)
### 安装sonar-scanner

[sonarScanner官网教程](https://docs.sonarqube.org/latest/analyzing-source-code/scanners/sonarscanner/)，docker方法没有试，我于window64位安装解压后，环境变量path添加bin之后安装成功
### 创建项目

![image-20230113140420129](https://s2.loli.net/2023/01/13/PLyBZIetKxmGwvF.png)

![image-20230113140445385](https://s2.loli.net/2023/01/13/D3t8BJOHTG67wax.png)

![image-20230113140459324](https://s2.loli.net/2023/01/13/57vKT4bAMFIBDUG.png)

![image-20230113140517877](https://s2.loli.net/2023/01/13/7t34QpvrUKsiwEl.png)

之后点击继续，其他按照教学走就可以

![image-20230113140552167](https://s2.loli.net/2023/01/13/jupwSxLglV5MG18.png)

	8.窗口运行之后返回[http://localhost:9000/](http://localhost:9000/)页面，可以看到bug

![image-20230113141351314](https://s2.loli.net/2023/01/13/QtyFKAz6BTGmXHr.png)
-