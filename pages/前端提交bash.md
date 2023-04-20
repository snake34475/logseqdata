- ```bash
  #!/bin/bash
  
  # 请将以下变量替换为远程服务器和 SSH 私钥文件的真实信息
  REMOTE_USER=root
  REMOTE_HOST=81.68.128.43
  REMOTE_DIR=/www/wwwroot/
  LOCAL_DIR=./navback.onestyle.top/
  SSH_KEY=./.bash_release/hp_omen.pem
  
  ##先自己执行打包
  echo "开始执行打包"
  wait $!
  npm run build
  wait $!
  rm -rf ./navback.onestyle.top
  wait $!
  mv dist navback.onestyle.top
  wait $!
  echo "打包完成"
  
  echo "执行scp传输"
  # 使用 scp 命令将本地 build 文件夹上传到远程服务器上
  scp -r -i $SSH_KEY $LOCAL_DIR $REMOTE_USER@$REMOTE_HOST:$REMOTE_DIR
  
  wait $!
  rm -rf ./navback.onestyle.top
  wait $!
  echo "scp传输执行完毕"
  
  #echo "执行git上传"
  
  git add .
  wait $!
  
  git commit -m "使用scp脚本更新"
  wait $!
  
  git push origin main
  wait $!
  echo "git上传执行完毕"
  
  echo "所有任务完成"
  
  
  ```
- npm run scp 执行