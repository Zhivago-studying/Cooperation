# 就是学git咯

## 常用命令

* git init  
  初始化
* git add .  
  添加
* git commit -m "xxx"  
  提交
* git status  
  查看状态
* git log  
  查看历史日志，（用git-log 更完整）
* git reflog
  查看所有操作记录,(用来在回退版本后，想反悔，查找当前版本之后的id)
* git reset --hard commitID  
  版本回退，commitID为commit的id号,可以用git log查看
* .gitignore  
  忽略文件,利用通配符列举要忽略的文件即可，#表示注释

## 分支

* git branch  
  查看分支，其实用git-log就行  
* git branch 分支名  
  创建分支
* git branch -d 分支名  
  删除分支
* git checkout -b 分支名  
  即创建并切换,其中git checkout 是切换分支， -b表示创建分支（branch），
* git merge 分支名  
  将该分支合并到当前分支，（所以一般先切换到master分支）
* 解决冲突  
  无脑冲进去，把有冲突的地方手动改成想要的，add、 commit即可.

## gitee 或 github

