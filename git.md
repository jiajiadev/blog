#git常用命令:
##1.基本命令
* git init :初始化仓库
* git status:查看当前状态
* git commit:提交
* git commit -am "init":提交并且加注释
* git commit -a:提交当前repos的所有改变
* git commit -a -v:一般提交命令
* git push origin  master:将文件推到服务器上
* git add [file name]:添加文件到仓库
* git log:查看历史记录
* git rm [file name]：从git中删除指定文件
* git clone:克隆仓库
* git config --list:查看所有用户
* git ls-files：看已经被提交的
* git diff:查看具体修改内容
##2.需要注意的地方
* 添加文件到仓库分两步：
第一步：使用git add [file name]，可反复使用，添加多个文件；第二步：使用git commit完成。
* 在git中，用HEAD表示当前版本，上一个版本就是HEAD^,上上一个版本就是HEAD^^,类似地，往上100个版本就是HEAD～100。使用git reset --hard commit_id可在版本间穿梭。
* git管理的是修改，不是文件。每次修改后：git add->git commit，如果不add到暂存区，就不会加入到commit中。
* 撤销修改：
第一种情况：改乱了工作区某个文件的内容，直接丢弃修改时，使用命令git checkout --file。
第二种情况：不但改乱了工作区某个文件的内容，还添加到了暂存区，丢弃修改分两步，第一步用git reset HEAD file，回到第一种情况。
* 关联一个远程库，使用命令git remote add origin git@sever-name:path/repo-name.git;关联后，使用命令 git push -u origin master第一次推送master分支的所有内容；此后，每次本地提交后，可使用git push origin master推送最新修改。
