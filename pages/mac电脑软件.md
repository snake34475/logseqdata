- 阿里的[apptoolkits](https://github.com/apptools-lab/AppToolkit) 可视化配置软件
- nvm,node,brew
- git
- vscode,谷歌浏览器
- 有道词典
- postman
- mongodb
- Night eyes safria浏览器显示暗黑
- typora (笔记) 坚果云 (云端更新笔记) xmind (思维导图)
- Dash 链接tabbar,办公文档神器
- clashX飞机
- Scroll Reverser 触控板和鼠标滚轮翻转
  
  12.sudo killall -STOP -c usbd     usb闪烁
### m1兼容性

node的话不兼容node15以下的版本，都是基于rosetta2 的 terminal 安装。15.x 以下的 nodejs 版本，推荐使用 Visual Studio Code - Insiders 来运行项目，15.x 及以上的 nodejs 版本，则直接使用默认的 Visual Studio Code 。
## 文件只读

mac中文件
## zsh
### 使用系统自带的 zsh

```
chsh -s /bin/zsh
```
### zsh 切换回 bash

```
chsh -s /bin/bash
```

bash 的环境变量是`.bash_profile`文件。
zsh 的环境变量是`.zshrc`文件。

PS：如果从 bash 切换到 zsh，但想保留 bash 所设置的环境变量，可在 `.zshrc`文件末尾添加 `source ~/.bash_profile` 保存退出，并重启终端即可使用 bash 的环境变量。
- ## brew下载
	- ```
	  /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
	  ```
	  
	  [mac bash终端显示分支名称](https://blog.csdn.net/qq_34497272/article/details/107437271)