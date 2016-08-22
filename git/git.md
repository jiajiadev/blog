#git常用命令:

##基本命令
* git init :初始化仓库
* git status:查看当前状态
* git commit:提交
* git commit -a -m "init":提交并且加注释
* git commit -a:提交当前repos的所有改变
* git commit -a -v:一般提交命令
* git add [file name]:添加文件到仓库
* git rm -r --cached [file name]：从git库中删除指定文件,保留本地文件
* git rm [file name]：从git库中删除指定文件
* git log:查看历史记录
* git clone:克隆仓库
* git config --list:查看所有用户的配置信息
* git ls-files：看已经被提交的文件
* git diff:查看具体修改内容

## Remote Repo
* git remote: list remote repos
* git remote -v : list remote repos in verbose mode
* git branch -r : list remote branches
* git push [remotename] [localbranch]:[remotebranch]: push localbranch to remotename/remotebranch, if the localbranch is not exist on remote repo that it will automatically create a new remote branch
* git push remotename :remotebranch: delete remotebranch before git version 1.7
* git push remotename --delete remotebranch: delete remotebranch on git version 1.7 and newer

## Local Repo
* git branch: list local branches 
* git branch <branch> : create a new branch
* git checkout <branch> : change current branch
* git merge <branch>: merge branch to current branch
* git branch -d <branch>: delete a local branch
* git branch -D <branch>: delete a local branch forcelly


##需要注意的地方
* 添加文件到仓库分两步：
第一步：使用git add [file name]，可反复使用，添加多个文件；第二步：使用git
commit完成。
* 在git中，用HEAD表示当前版本，上一个版本就是HEAD^,上上一个版本就是HEAD^^,类似地，往上100个版本就是HEAD～100。使用git
  reset --hard commit_id可在版本间穿梭。
* git管理的是修改，不是文件。每次修改后：git add->git
  commit，如果不add到暂存区，就不会加入到commit中。
* 撤销修改：
第一种情况：改乱了工作区某个文件的内容，直接丢弃修改时，使用命令git checkout --file。
第二种情况：不但改乱了工作区某个文件的内容，还添加到了暂存区，丢弃修改分两步，第一步用git reset HEAD file，回到第一种情况。
* 关联一个远程库，使用命令git remote add origin
  git@sever-name:path/repo-name.git;关联后，使用命令 git push -u origin
master第一次推送master分支的所有内容；此后，每次本地提交后，可使用git push
origin master推送最新修改。
