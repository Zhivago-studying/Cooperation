# git note

## git init

将当前文件夹变为git可以管理的仓库

## git add 文件名

将文件加入暂存库

## git commit -m "说明"

更改提交到版本库

## git status

查看当前git状态

## git diff

查看当前的修改

## git log

查看提交的历史记录

## git reset --hard HEAD^

+ 退回前一个版本  
+ HEAD 表当前版本，加一个^ 就前一个版本，HEAD~100 表示前100个版本  
+ --hard 表回退到上个版本的已提交状态，--soft 会回退到上个版本的未提交状态, --mixed会回退到上个版本已添加但未提交的状态
+ 将HEAD换成版本号，仅需输入前几位即可

## git reflog

查看历史命令，可以用来找到版本号

## git diff HEAD -- 文件名

查看工作区和版本库里面最新版本的区别

## git checkout -- 文件名

可以丢弃工作区的修改，但不能对暂存区作用

## git reset HEAD 文件名

可以把暂存区的修改撤销掉

## git rm 文件名

+ 删除文件（提交至暂存区）  
+ 用rm删除文件后，用 git add 文件名,效果同
+ 然后commit就行

## 生成密钥

```$ ssh-keygen -t rsa -C "youremail@example.com"```  
添加密钥  
用户主目录隐藏文件中，会出现.ssh文件  
里面id_rsa和id_rsa.pub分别为私钥和公钥

## 关联远程仓库

```$ git remote add origin git@github.com:用户名/仓库名.git```  
在github上关联远程仓库  
```$ git push -u origin master```  
推送到远端，其实完整语法是 ```$ git push -u 远端仓库名 本地分支名:远端分支名```
-u 将本地master与远程库中的master关联，以后不用加-u，直接git push,即可将本地的提交推送至远程库

## 删除远程仓库

+ ```git remote -v``` 查看远程库信息  
+ ```git remote rm 远程库名``` 删除远程库（实际上只是解除关联，摧毁远程库需到github）

## 从远程库克隆

```$ git clone git@github.com:用户名/库名.git```

## 创建分支

```$ git checkout -b 分支名```创建并切换  
```$ git switch -c 分支名```创建并切换  
```$ git branch 分支名```创建  
```$ git checkout 分支名```切换  
```$ git switch 分支名```切换  
```$ git branch```查看分支  
```$ git merge 分支名```合并到某分支  
```$ git branch -d 分支名```删除分支

## 解决冲突

存在冲突时需手动解决冲突然后提交  
```$ git log --graph```命令可以看到分支合并图  

## 禁用fast forward

```$ git merge --no-ff -m "merge with no-ff" dev```  
强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息

## 临时储存当前工作

+ ```$ git stash``` 储存工作  
+ ```$ git stash list``` 查看储存的工作  
+ ```git stash apply```恢复，但是恢复后，stash内容并不删除，你需要用```git stash drop```来删除  
+ ```git stash pop```恢复的同时把stash内容也删了
+ ```$ git stash apply stash@{0}```恢复指定的stash

## 复制其他分支的提交过来

```$ git cherry-pick 提交号```

## 抓取远程分支

+ 默认只能克隆master  
+ ```git checkout -b dev origin/dev```可以创建远程origin的dev分支到本地
+ 提交有冲突时，先抓取最新提交下来，解决冲突后本地合并提交```git pull```,如果失败就按照提示指定链接

## 标签管理

+ ```$ git tag v1.0```将当前分支的最新提交打一个v1.0的标签（加 -m " "，可以添加说明）  
+ ```git tag```查看所有标签  
+ ```$ git tag v0.9 提交号```将对应提交打上标签  
+ ```git show 标签名```显示详细信息  
+ 推送标签与推送提交一致 ```$ git push origin --tags``` 一次性推送所有标签  
+ ```git tag -d 标签名```删除  
+ ```$ git push origin :refs/tags/v0.9```从远程库删除标签
