# git常用命令:

## 本地库的操作

查看当前状态
```bash
$ git status
```
  
提交并添加注释
```bash
$ git commit -a -m "related message"
```
  
添加文件到仓库  
```bash
$ git add [file name]
```
  
从git库中删除指定文件,保留本地文件  
```bash
$ git rm -r --cached [file name]
```
  
查看具体修改内容  
```bash
$ git diff
```
  
列出本地分支（List local branches）  
```bash
$ git branch
```
  
创建一个新的分支（Create a new branch）  
```bash
$ git branch [new branch name]
```
  
切换当前所在分支（Change current branch）  
```bash
$ git checkout [branch name]
```
  
合并其它分支到当前分支（Merge branch to current branch）  
```bash
$ git merge [branch name]
```
  
删除指定分支（Delete a local branch）  
```bash
$ git branch -d [branch name]
```

查看更新日志  
```bash
$ git log
$ git log --oneline 
$ git log --stat   
```

## 远程库的操作 

列出远程库（List remote repos in verbose mode）: 
```bash
$ git remote -v
```

列出远程分支（List remote branches）:
```bash
$ git branch -r
```

下载远程库的分支并与本地分支合并（Fetch remote branch and merge into current local branch）: 
```bash
$ git pull [remote repo name] [remote branch name]
```

提交本地分支到远程库，如果分支名不存在，则在远程库中创建该分支（Push local
branch to remote repo, if the local branch is not exist on remote repo that it
will automatically create a new remote branch）:
```bash
$ git push [remote repo name] [local branch name]
```

添加远程库（Add remote）: 
```bash
$ git remote add [name] <url>
```
默认的远程库的名称是origin（Default name is "origin"）

删除远程库（Remove remote）: 
```bash
$ git remote rm <name>
```

重命名远程库（Rename remote）: 
```bash
$ git remote rename <old> <new>
```


## See also

[Git tutorial on github](https://github.com/geeeeeeeeek/git-recipes/wiki/2.4-%E6%A3%80%E6%9F%A5%E4%BB%93%E5%BA%93%E7%8A%B6%E6%80%81)

##需要注意的地方
* 在git中，用HEAD表示当前版本，上一个版本就是HEAD^,上上一个版本就是HEAD^^,类似地，往上100个版本就是HEAD～100。使用
```bash
$ git reset --hard commit_id
```
可在版本间穿梭。

* 撤销修改：
第一种情况：改乱了工作区某个文件的内容，直接丢弃修改时，使用命令
```bash
$ git checkout --file。
```

第二种情况：不但改乱了工作区某个文件的内容，还添加到了暂存区，丢弃修改分两步，第一步用
```bash
$ git reset HEAD file
```
回到第一种情况。

