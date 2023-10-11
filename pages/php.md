- php基础
	- php为弱类型语言，不必声明数据类型
	- ```php
	  <?php
	  $txt="Hello world!";
	  $x=5;
	  $y=10.5;
	  ?>
	  ```
	- 作用域
		- ```
		    $GLOBALS['y']=$GLOBALS['x']+$GLOBALS['y'];
		     static $x=0; 声明的变量不需要删除
		  ```