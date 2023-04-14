- 百度网盘下载 [链接](https://pan.baidu.com/s/1XSjBZ6U3OiVZULEjvJbd2g?pwd=tvmc)
- 打开后将所有的包解压，我们可以看到
  ![Replaced by Image Uploader](https://s2.loli.net/2023/04/14/CLvU65PjMbStNmx.png)
- 打开`3-20日更新`这个包,可以看到`chatglm-6b`这个文件夹，将这个文件夹内部的所有文件拷贝覆盖到model文件中的`chatglm-6b`中
  ![Replaced by Image Uploader](https://s2.loli.net/2023/04/14/Sk6b3cH5lpL82Fn.png){:height 141, :width 533}
  ![Replaced by Image Uploader](https://s2.loli.net/2023/04/14/vPjEHn5cra9b1W2.png)
- 将解压好的`model`放到`ChatGLM-webui`文件中
- 将环境包内部的文件粘贴到`ChatGLM-webui`文件中
- 最终展示为
  ![Replaced by Image Uploader](https://s2.loli.net/2023/04/14/bwF6EtXlOihqADV.png){:height 286, :width 533}
- 此时点下强制更新，更新下最新代码
- 然后根据自己的显存选项选择使用哪个脚本
   ![Replaced by Image Uploader](https://s2.loli.net/2023/04/14/axS5vIfuK9yNFqe.png)
- 8g的显存点击运行
-
- 报错分析
	- ![image.png](../assets/image_1681450326814_0.png){:height 300, :width 503}
		- 点击同文件想的install.sh尝试
		- 重新按照以上步骤安装
		- 重启电脑
		-
	- `Symbol cudaLaunchKernel not found`
		- 可以尝试
		- 这种一般是int4 也就是显存小于8g的时候的报错，需要单独安装 [cuda](https://developer.nvidia.com/cuda-downloads)
-
-