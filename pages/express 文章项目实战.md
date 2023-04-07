- 初始化项目
  首先新建一个项目文件夹，之后在内部执行命令
  ```bash
      npx express-generator
  	cd server
      npm install
      SET DEBUG = server:* & npm start
  ```
- 1. 安装并连接redis
  `npm install redis –save`
  2. 新建config文件命名db.js
  ```js
       exports.redisConfig = {host: '127.0.0.1', port: '6379', ttl: 5 * 60 * 1000}
  ```
  3.utils文件新建redisDB.js文件
  [[express项目-redisDB.js]]
-
-
-