- ```bash
  # cli
  # 创建项目
  $ npm i -g @nestjs/cli
  $ nest new project-name
  
  # 内置验证crud
  $ nest g resource [name]
  # 创建控制器
  $ nest g controller [name] 
  # 创建服务
  $ nest g service [name] 
  # 创建模块
  $ nest g module cats 
  
  ```
- ## [Controllers](https://docs.nestjs.com/controllers)
	- 处理请求接收到的请求，并返回给客户端，需要在modules中注册，否则映射不起作用
	- 使用第三方库例express时，需使用passthrough，否则无法使用拦截器Header
	- ```js
	  //处理get请求的query参数
	  @Get('docs')
	  @Redirect('https://docs.nestjs.com', 302)
	  getDocs(@Query('version') version) {
	    if (version && version === '5') {
	      return { url: 'https://docs.nestjs.com/v5/' };
	    }
	  }
	  
	  //get请求的params参数
	  @Get(':id')
	  findOne(@Param('id') id: string): string {
	    return `This action returns a #${id} cat`;
	  }
	  
	  //post请求
	  export class CreateCatDto {
	    name: string;
	    age: number;
	    breed: string;
	  }
	  @Post()
	  async create(@Body() createCatDto: CreateCatDto) {
	    return 'This action adds a new cat';
	  }
	  ```
- ## [Provider](https://docs.nestjs.com/providers)
  id:: 65658a10-a5bb-4e7a-8a75-28493ded307e
	- nest基本概念，服务，资源库，工厂等基类可以认为是provider，主要理念是**依赖注入**
	- 和controller一起使用时，controller用于处理http请求，复杂的tasks给providers去进行
	- 原文写的比较好，此处不贴代码了，其实就是在provider中构建好基类，然后controller里面去实现这个类，好处是当调用这个方法的时候，如果之前没new就直接new，如果new过了就用之前的，和连接池有点像
	- promise
		- ```js
		    @Get()
		    async findAll(): Promise<Cat[]> {
		      return this.catsService.findAll();
		    }
		  ```
- ## [Modules](https://docs.nestjs.com/modules)
	- 模块就是应用程序的基本结构，你可以认为整个应用程序就是一个模块，例如app.modules，然后你可以在app.modules里面引入其他小模块
	- 小模块导出使用exports导出，引入使用import
	- 共享实例，可以export服务，然后在其他模块引入模块之后可以共享实例
	- 考虑下动态模块如何使用