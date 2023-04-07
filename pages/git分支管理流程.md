## Github Flow

	轻量化分支管理方案,适用于开发者比较多，需要频繁发布的项目

	1）创建分支，master不允许修改，并且可以随时运行。需要修改从master签出新的分支，分支名可以根据功能名命名

	2）提交代码，提倡频繁提交代码，例如每次新增，修改一个文件都可以提交，并且注释，方便出现bug进行回滚，也方便后续开发者快速了解分支内容

	3）开启拉取请求，专业术语为"Pull Request" 简称PR，这一步很重要，开发者可以向目标分支发起PR，此时开发者可以看到，一般在功能完成之后，但如果在开发过程中遇到问题可以开启PR并且@其他开发者获取帮助

	4）讨论和回顾代码，如果需要其他开发者进行协助，代码审核是否符合项目的开发规范和必须的单元测试等

	5）部署和测试代码，代码被合并之前必须确认是可执行的，没有明显的bug，并且测试代码和测试覆盖率能顺利通过。

	6）合并分支，合并之后，与之关联的issue会被关闭
## Git Flow

git默认的工作流程

	1）创建分支

```
$ git flow init
```

将会默认创建master和develop
	- master，并不能直接提交代码，而是在其他指定的分支中修改和提交
	- develop分支，是任何新开发的基础分支，该分支聚积了所有已完成的功能，等待整合到master分支中
	  
	  	这两个是长期分支，会存活整个生命周期，其他进行功能或者发行的分支只是临时存在的，完成之后自行删除
	  
	  	2）功能开发，创建一个新的feature分支
	  
	  ```
	  #创建feature
	  git flow feature start xxx
	  #开发完成后合并到develop分支
	  git flow feature finish xxx
	  ```
	  
	  	3）代码发布
	  
	  	develop分支聚积足够多的功能并且已经被测试和修复之后，就可以进行发布
	  
	  ```
	  git flow release start x.x.x
	  ```
	  
	  	start之后一般是以‘.’相隔的3位数版本号，此时会从develop分支签出一个新的分支，完成版本号修改后执行完成
	  
	  	4）代码修复
	  
	  	master运行时候遇到bug，通过创建新的分支来修复
	  
	  ```
	  git flow hotfix start xxxx
	  ​
	  # 完成改动后修复bug的分支会被合并到master分支和develop分支中，同时删除该分支并切换到develop分支
	  git flow hotfix finish xxxx
	  ```
## GitLab Flow

	GIt Flow至少存在两大问题
- master分支被削弱，都是基于develop分支进行开发，develop分支只是用来部署可运行的代码，开发工具和git仓库都是默认master所以需要频繁切换分支
- 分支种类复杂，大量时间花费在创建分支，合并分支和销毁分支这些与开发无关的重复操作，同时容易出现错误
  
  	所以退出github flow方案，但是也存在一些问题，例如部署，环境设置，发布，和issue管理等
  
  	gitlab避免出现的问题，取消develop分支，采取基于master签出和合并的策略，同时将issue和feature分支紧密结合
  
  流程如下
  
  	1）规划好master、pre-production、preoduction分支，master用于签出代码和合并代码，pre-preduction 从master分支签出，用于发布到预发布环境（测试环境）；production分支从pre-production分支签出，用于部署到线上环境
  
  	2）每次开发或修复bug，先创建issue，声明分支的主要作用和需要修改的代码，从master签出的分支，命名必须以之前创建的issue编号开头，然后再次分支上进行开发，这样好处是代码合并到master分支之后改对应的编号的issue就会自动关闭
  
  	3）feature分支开发完成之后使用rebase命令合并多个commits记录，防止commits记录混乱，执行完后再push到远程分支，同时提Merge Request
  
  	4）对代码进行检查和测试，通过后合并master分支，此时master分支处于可测试，可运行，可部署到开发环境进行测试
  
  	5）master分支测试通过，删除feature分支，同时向pre-production分支发起Merge Request进行测试，通过后向production发起Merge Request，合并后更新线上，如果分支遇到紧急更新，可以不删除feature分支，直接feature合并到pre-production进行测试