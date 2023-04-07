- 初始化项目
  首先新建一个项目文件夹，之后在内部执行命令
  ```bash
      npx express-generator
  	cd server
      npm install
      SET DEBUG = server:* & npm start
  ```
- 安装并连接redis
  `npm install redis –save`
- 新建js文件命名config db.js