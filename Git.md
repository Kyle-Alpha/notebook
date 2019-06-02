**1.下载git**

$ sudo apt-get install git

**2.配置git**

$ git config --global user.name "Your Name"

$ git config --global user.email "email@example.com"

**3.创建test本地库**

$ git init test

**4.添加文件至本地仓库**

$ vi readme.txt
$ git add readme.txt

$ git commit -m"readme.txt"

**5.git clone远端服务器上的仓库**

$git clone username@host:/path/to/repository

**6.推送改动**

$ git push origin master

**7.分支**

**创建一个叫做“feature_x”的分支，并切换过去：**

$ git checkout -b feature_x

**切换回主分支：**

$ git checkout master

**再把新建的分支删掉：**

$ git branch -d feature_x

**除非你将分支推送到远端仓库，不然该分支就是 不为他人所见的：**

$ git push origin <branch>

**8.更新本地仓库**

$ git pull origin master

**以在你的工作目录中 获取（fetch） 并 合并（merge） 远端的改动。**
**要合并其他分支到你的当前分支（例如 master），执行：**

创建分支

$ git branch <name>

切换分支

$ git checkout <name>

创建加切换分支

$ git checkout -b <name>



删除分支

$ git branch -d <name>

切换master分支

$ git checkout master

合并分支

$ git merge <branch>

$ git add <filename>

**在合并改动之前，也可以使用如下命令查看：**

$ git diff <source_branch> <target_branch>

**9.替换掉本地改动**

$ git checkout -- <filename>

10.**丢弃你所有的本地改动与提交，可以到服务器上获取最新的版本并将你本地主分支指向到它**

$ git fetch origin

$ git reset --hard origin/master

**11.版本控制**

$ git reset --hard HEAD^

$ git reset --hard HEAD~20

$ git reset --hard xxxxx

查看操作记录

$ git reflog

$ git log

查看工作区状态

$ git status

撤销工作区改动

$ git checkout --xx.txt

对比文件

$ git diff HEAD HEAD^ -- xx.txt