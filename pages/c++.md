- 基础模板
	- ```cpp
	  //基础格式
	  #include<iosteam>;
	  using namespace std;
	  
	  int main(){
	    
	    int a;
	    cout << "请输入a的值" << endl;
	    cint >> a;
	    cout << "a的值为：" << a << endl;
	    
	    system("pause");
	    return 0;
	  }
	  
	  cout << endl; //换行
	  ```
- 基础
	- 算数运算符
		- 递增递减
			- 前值递增是先加一再运算
			- 后置递增是先运算再递增
		- 比较运算符
			- 比较运算符的结果是1或0
		- 跳转语句
			- break 之后for循环不执行
			- continue 跳过continue本次的，其他继续执行
			- goto 不推荐使用
				- 跳到指定循环
				- ![Replaced by Image Uploader](https://s2.loli.net/2023/10/22/HTYk2lCDsUjApcy.png)
				- ![Replaced by Image Uploader](https://s2.loli.net/2023/10/22/Mod5LG82JxhWwF9.png)
	- 数据类型
		- 数组
			- ```cpp
			  int arr[5];
			  int arr [1] = {1};
			  
			  ```