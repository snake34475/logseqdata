- #docker
- 1.基础配置
	- 指定用什么镜像，工作目录，安装依赖
	- Dockerfile
		- ```Dockerfile
		  # 使用 Node.js 作为基础镜像
		  FROM node:16
		  
		  # 设置工作目录
		  WORKDIR /app
		  
		  COPY package*.json ./
		  
		  # 安装项目依赖
		  RUN npm install
		  
		  # 构建生产环境静态文件
		  # RUN npm run build
		  
		  # 设置容器启动命令
		  # CMD ["npm","run" ,"serve"]
		  # ENV CHOKIDAR_USEPOLLING=true 
		  ```
	- docker-compose.yml
		- port项目端口 宿主端口:项目真实端口
		- volumes 挂载目录 宿主目录:真实目录
		- ```yml
		  version: '3'
		  services:
		    frontend:
		      build:
		        context: .
		        dockerfile: Dockerfile
		      ports:
		        - 8081:8080 
		      volumes:
		        - .:/app
		      command: npm run serve --poll
		  ```
	- webpack监听更新
		- ```js
		  //webpack.config.js
		  //vue.config.js 这两者都可以放进去
		  devServer: {
		    port: 80, // 设置项目端口
		    host: '0.0.0.0', // 接受来自外部的链接，此处可以省略
		    watchOptions: {
		        aggregateTimeout: 500, //聚合延时
		        poll: 1000, // enable polling since fsevents are not supported in docker
		   	   ignored:/node_modules/
		    }
		  }
		  ```
		- `aggregateTimeout`:第一个文件更改，重建前增加延迟，会将这个这段时间内的所有更改都聚合在一次构建，毫秒为单位
		- `ignored`:排除
			- 正则 `/node_modules/`
				- 经尝试，不添加这个11800cpu会在百分之20-40左右，加上之后会降到20以下
			- 数组 `['**/files/**/*.js', '**/node_modules']`
		- `poll`：多少毫秒检查一次变动，传true则开启，默认为5007
-