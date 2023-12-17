- [LearnGitBranching游戏项目](https://github.com/pcottle/learnGitBranching)
- HEAD
	- HEAD 当前分支最新提交的指针或引用
	  通常指向两个不同的对象
		- 提交，某个分支上进行提交，他就指向这个分支的最新提交
		- 分支，切换新分支，那么就指向最新的分支
	- 创建新的提交，那么HEAD会移动到新的提交上，可通过git log查看提交历史
	- 综合实践来想，在代码回滚的时候，我们会使用git log查看代码的提交记录，然后将HEAD 移动到了那个提交记录，然后强制提交从而实现了回滚。
	-
- ```bash
  //合并两种方式
  git merge 
  git rebase
  
  //改变HEAD指向
  git checkout 分支/hash提交记录
  //改变分支指向
  git branch -f 分支名称 分支/hash提交记录
  
  git checkout HEAD //切换到当前引用
  git checkout HEAD^ //切换到当前提交的上次提交 通常用于回滚
  git checkout HEAD~<num> //切换到当前提交的第前几次提交
  
  //撤销本地分支
  git reset HEAD^
  //撤销远程提交 !!!请注意，变更本地是HEAD，变更远程是HEAD^
  git revert HEAD
  //复制某个提交到当前的分支
  git cherry-pick 分支/提交 
  
  ```