- nodejs创始人 Ryan Dahl
- deno创始人 Ryan Dahl
- [cnode](https://cnodejs.org/) nodejs专业中文社区
-
- web标准
	- WHATWG
		- 全称 web Hypertext application Technology working group (网络超文本应用技术工作组)
		- 是针对HTML相关技术的工作组创创立的，为了推动web发展，特别关注浏览器实现和开发需求，最著名是HTML Living Standard（HTML5的维护版本）。WHATWG的成员包括各大浏览器厂商，如谷歌、苹果、微软等。
	- W3C
		- 全称Word Wide web Consortium （万维网联盟）
		- 成立于1994，由互联网先驱 Tim berners-Lee创建
		- 负责指定和发布一系列web标准包，括HTML、CSS、XML、Web服务、安全性等方面的标准。W3C采用开放的工作组制度，会员包括各个领域的组织和个人。
-
- Runtime（运行时）更多的解释请看 [运行时（runtime）是什么意思？应该怎样深入且直观地理解？ - doodlewind的回答 - 知乎](https://www.zhihu.com/question/20607178/answer/2133648600)
  id:: 6549c9eb-bb4c-4a4f-810b-ce241d421fca
	- 程序运行时：指程序生命周期的阶段
	- 运行时库：例如glibc原生语言的标准库
	- 运行时[[系统]]：某门语言的宿主环境，例如 nodejs是js的运行时
	- runtime描述程序运行时执行的指令
- esm和cjs
	- esm是官方的导入导出
	- cjs是社区中开发的commonjs，主要用于服务端
- crud
	- 创建create、读取read、更新update、删除delete
- 技术
	- [Next.js](https://nextjs.org)
		- 用来构建现代化react应用程序的框架，强调性能和seo优化
		- 服务端渲染
		- 路由和数据预加载
	- [NestJS](https://nestjs.com)
		- 构建高效的的[[后端]]应用框架
	- [Nuxt.js](https://nuxtjs.org)
		- 构建优雅的vuejs应用程序框架，
		- 服务端渲染，异步加载
	- [deno](https://deno.com/)
		- 他是写服务端js的全新方法，和nodejs相似，写小工具可以
		- 下一代js运行时 ts和jsx支持 向后兼容nodejs 使用rust和tokio实现异步io
		- 具有权限控制，只能访问明确授权的文件，网络和环境变量
		- 可以使用浏览器的导入导出 import和export
	- [bun.js](https://bun.sh/)
		- [Bun 1.0 正式发布，爆火的前端运行时，速度遥遥领先！](https://juejin.cn/post/7277387014046335010)
		- 消除js工具链的缓慢和复杂，保留js本身优点，自身能够替代nodejs，转义器babel，构建工具webpack，包管理兼容，速度特别快，比nodejs快四倍，内置websocket支持，内置sqlit支持
		- 发布与2022年9月8日 部分node功能没有做完
	- [winterCG](https://wintercg.org/)
		- cloudfalre，nodejs，deno合作的社区组,致力于让不同的js运行时便携可移植代码，包括浏览器，服务端，嵌入式等
		- 目前定位是与现在webapi标准规范组织合作（WHATWG，W3C）合作，统一浏览器端和非浏览器端
	- rust
		- node在前端开发环境工具链上慢慢被rust吃掉，能用rust重写的npm都会用rust重写一遍
	- ORM库
		- orm是 Object-Relational Mapping 对象关系映射的缩写，简化与数据库的交互
		- [Prisma](https://www.prisma.io/)
			- 开发团队很倔，UTC 时间问题，Transcation 问题这些硬伤就是不解决。但是他们有资本投入有开发团队
			- 文档很垃圾
		- [typeorm](https://typeorm.bootcss.com/)据说好用
	- find-my-way
		- 快速的http路由框架 基于radix tree开发的路由框架，支持路由参数通配符
		- [find-my-way nodejs 快速的http 路由框架](https://www.cnblogs.com/rongfengliang/p/17495967.html)
	- [fastify](https://www.fastify.cn/)
		- 快速低消的web框架，专为nodejs打造
	- 网络方式
		- tRPC
			- 全称：Transient receptor potential canonical
			  全栈必定要学的，是一个库
			  远程过程调用框架，解决了全栈应用程序端对端安全性问题，在简化客户端和服务端之间的通信过程，提供高效的类型安全，允许使用本地函数调用方式来调用远程函数
			- 只有在next，nuxt，等项目中使用ts时，trpc才会有此优势
			- 构建端对端类型安全的api
		- REST（我们常用的是这种）
			- 全称 Representational State Transfer 表述性状态传递,
			- 使用get，post等动词来操作资源，允许客户端指定需要的数据，优点是方便理解，
		- GraphQL
			- 是一门查询语言,优点是减少网络请求次数，提高传输效率
			- 作为REST事实上的继承者
			- graphql是查询语言，允许客户端定义数据结构和字段，通过发送GraphQL查询来指定红藕徐的数据，[[服务器]]返回相应的数据，有点像[[前端]]直接写查询，[[后端]]直接提供[[数据库]]一样
			- ```js
			  //以下为一个案例
			  query {
			    user(id: 123) {
			      name
			      email
			      posts {
			        title
			        content
			      }
			    }
			  }
			  ```
- 关于nodejs的部分关键字
	- 阿里巴巴技术专家的话
		- node非常[[健康]]，凉的是web2
		  cjs和esm还不能互通有无，搞个ts配置都能烦死
		  找一个crud，都没好用的
		  和用react全栈的crud更是没有，可是有next
		  天天吹低码，却连rails都没有打败
		  从deno到bun，到wintercg，竟不知定制的上线
		  从find-my-way到fastify，ts刚搞完，装饰器路还远，
		  各种orm满天飞，分布式事务还没有好的库
		  自己实现http1.1，自己搞test，无非生态内容被抓到core，
		  cnode不够活跃，都跑到掘金知乎，看看
		  这些后起之秀，前辈们都已经在晒沙滩浴了。
		  一代目空无，朋春，朴灵，苏千
		  二代目alsotang，死马，张挺，九十，秦粤，死月，黄一君，年翼，霸剑，天猪
	- node在[[前端]]开发环境工具链上慢慢被rust吃掉，能用rust重写的npm都会用rust重写一遍
	- 有个trpc框架配合next写crud
	- nestjs+nx+nexts
		- 一个monorepo的工具 nx.dev
	- [2023年nodejs凉了吗？凉到什么程度了？ - 黑马程序员前端的回答 - 知乎](https://www.zhihu.com/question/597238130/answer/3192764176)