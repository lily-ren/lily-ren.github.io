---
title: git的基础命令
tag: ./
---​  
<h2><center>git基础指令</center></h2>

---

- git     查看是否存在及版本
- git init     把目录变成github可以管理的仓库
- git add 文件名     把工作区的文件添加到github仓库的暂存区
- git commit -m “本次提交说明”     把暂存区的文件提交给分支。可add多次再一次commit     一步到位：git commit -am “本次提交说明”
- git status     查看仓库状态
- git diff 文件名     查看与上次提交的有什么不同 （Mac上一般使用vscode或者 sourceTree来查看版本的不同。）
- git log     显示从最近到最远的提交历史​
- git log --pretty=oneline     显示从最近到最远的提交日志的版本号
- git log --graph     看到分支合并图
- git reset --hard HEAD^或commit_id     git中用HEAD表示当前版本，HEAD^上一个版本，HEAD^^上上个版本；版本号写前几位就可以
- git reflog     查看每条历史命令
- git restore 文件名     丢弃工作区的改动
- git reset HEAD 文件名     把暂存区的修改撤销掉，重新放回工作区
- git remote add origin git@git.com: 我的github账户名/远程上要用的空仓库名.git     把本地仓库的内容推送到GitHub仓库
- git clone git@git.com: 我的github账户名/远程上要用的仓库名.git     把远程库克隆到本地库
- git remote set-url origin git@git.com: 新地址/仓库.git     更改远程仓库新指向
-  git push     把本地库的内容推送到远程
- git push 远程主机名 本地分支名: 远程分支名     把本地分支的内容推送到远程指定分支​
- git checkout -b 分支名     创建分支并切换
- git switch -c 分支名     创建分支并切换。相当于git branch 分支名（创建分支） + git checkout 分支名（切换分支）/ git switch 分支名
- git branch     查看当前分支  -a显示所有分支  -r显示远程分支  -d删除分支  -D 强行删除分支
- git merge 分支名     合并指定分支（写的分支名）到当前分支
- git branch -d 分支名     删除制定分支（写的分支名）
- git fetch 远程主机名      将某个远程主机的更新全部取回本地
- git fetch 远程主机名 分支名     只想取回特定分支的更新
- git pull 远程主机名 远程分支名: 本地分支名     将远程主机的某个分支的更新取回，并与本地指定的分支合并（如果远程分支是与当前分支合并，则冒号后面的部分可以省略）

- git pull相当于  git fetch origin master   //从远程主机的master分支拉取最新内
- git merge FETCH_HEAD    //将拉取下来的最新内容合并到当前所在的分支中
- git merge 分支名     合并分支上的内容到本地来

​    注：拉取后也要push，时刻铭记远程-本地-远程的原则

#### 开发步骤：

​    1：克隆代码     git clone git@git.com: 我的github账户名/远程上要用的仓库名.git

​    2：查看所有分支     git branch --all 

​    3：创建本地新的dev分支     git branch 分支名   #创建本地分支

​    4：发布dev分支     git push origin dev:dev  #同步dev分支的代码到远程服务器，这样远程仓库也有一个dev分支了。

​    5：在dev分支开发代码

- git checkout dev  # 切换到dev分支进行开发

- \# 开发代码之后，我们有两个选择

- \# 第一个：如果功能开发完成了，可以合并主分支

- git checkout master  # 切换到主分支

- git merge dev  # 把dev分支的更改和master合并

- git push  # 提交主分支代码远程

- git checkout dev  # 切换到dev远程分支

- git push  # 提交dev分支到远程

- \# 第二个：如果功能没有完成，可以直接推送

- git push  # 提交到dev远程分支

- \# 注意：在分支切换之前最好先commit全部的改变，除非你真的知道自己在做什么。

​    6：删除分支

- git push origin :dev  # 删除远程dev分支，危险命令哦

- \# 下面两条是删除本地分支

- git checkout master  # 切换到master分支

- git branch -d dev  # 删除本地dev分支

#### 新建自己的git仓库：

  1：mkdir 文件名 --  创建新文件  cd去到当前文件的路径下，使用pwd检查文件路径。

  2：初始化  当前路径下 git init 把当前目录变成git可以管理的仓库

  3：添加文件   使用git add + 文件名，将文件添加到仓库。（添加到仓库的暂存区）

​     提交文件   使用git commit -m +文件提交情况说明，将文件提交到仓库。。可add(将文件添加到暂存区中)多次再一次commit（提交到分支上）     一步到位：git commit -am “本次提交说明”

  4: 查看修改状况   git status  如果有更改，会显示 modified

​      不记得修改了哪里，就可以使用source tree来查看对比上次提交修改了哪些地方。 

  5: 版本检查：source tree中的分支可以直接查看提交的版本。（git log）

  6: 文件版本退回：git reset --        退回后，新加的版本就没有了，但是可以通过hard找回  git reset --hard HEAD  （指向当前版本）

​      git中用HEAD表示当前版本，HEAD^上一个版本，HEAD^^上上个版本；版本号写前几位就可以

  7: 删除文本：git rm + 文件名   恢复是？？？checkout 为什么没有用

  8: 创建公钥

  

  9: 在github上创建一个远程库，然后使用git remote add origin git@github.com: 用户名/仓库名.git

  与远程的仓库链接。      第一次再使用git push -u origin master，把前面推进仓库的文件发送到远程仓库去。

*master是git为我们自动创建的第一条分支。

*nvm alias default 8.12.0 //设置默认的node版本（以后都不用改的那种）

![git导图](git.png)
