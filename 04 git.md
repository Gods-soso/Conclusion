## git 分布式版本控制

+ git init:将该文件交给git管理
+ git status:查看文件状态
+  .gitignore,要忽略哪些文件，即不想让git管理的文件，在.gitignore中写上该文件名
+ 工作区到暂存区
   +  git add .
   +  git add 文件名
   +  git add 文件夹名/
+ 暂存区到工作区
   +  git rm --cached 文件名 （从暂存区删除）
   +  git checkout -- 文件名 （从暂存区复制一份文件替换工作区的文件，暂存区里的文件不会动）
+ 暂存区到本地仓库
   +  git commit -m "信息描述"  （生成历史版本） 
   +  git log  或 git reflog  (查看版本信息)
   +  git reset --hard 版本号   （回到哪一个版本）
   +  git reset HEAD -- 文件路径  ==>作业:拉取最近一次提交到版本库的文件到暂存区,该操作不影响工作区
   +  git commit --amend -m "信息描述"  （撤销上一次提交的版本,并将暂存区文件重新提交）
+ 分支操作
   +  git branch 分支名  （创建分支）    
   +  git checkout 分支名  （切换分支）
   +  git branch   (查看分支)
   +  git branch -d 分支名  （删除分支）
   +  git merge 分支名 -m "信息描述"  （合并分支）
+ 远程仓库: github
   +  git remote add 别名 远程仓库的https地址 (给该仓库地址取个名)
   +  git push 别名 分支名 
   +  git pull 远程仓库地址 (下载到本地，下载过)
   +  git clone 远程仓库地址 (下载到本地，未下载过)