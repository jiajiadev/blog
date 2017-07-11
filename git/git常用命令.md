# git常用命令:

## 本地库的操作

* 查看当前状态
    `git status`
* 提交并添加注释
    `git commit -a -m "related message"`
* 添加文件到仓库
    `git add [file name]`
* 从git库中删除指定文件,保留本地文件
    `git rm -r --cached [file name]`
* 查看具体修改内容
    `git diff`
* List local branches
    `git branch`
* Create a new branch
    `git branch [new branch name]` 
* Change current branch
    `git checkout [branch name]`
* Merge branch to current branch
    `git merge`
* Delete a local branch 
    `git branch -d` 

## 远程库的操作 
* List remote repos in verbose mode
    `git remote -v`
* List remote branches
    `git branch -r`
* Fetch remote branch and merge into current local branch
    `git pull [remote repo name] [remote branch name]`
* Push local branch to remote repo, if the local branch is not exist on remote repo that it will automatically create a new remote branch
    `git push [remote repo name] [local branch name]`

// syxbyi97 added below on Jun 30th, 2017
// 英语渣欢迎纠正…………

# Git

## Clone
### Common clone

Clone and create a remote host: 
```bash
$ git clone <url> [directory]
```
Default remote named "origin". 

The newest commitment only: 
```bash
$ git clone -b master --depth=1
```

### Other clone
Point out remote host: 
```bash
$ git clone -o <remote_name> <url> [directory]
```

## Log
### Common log

Limit the displayed lines : 

```bash
$ git log -<limit_num>
```

Print each log in one line : 

```bash
$ git log --oneline
```

Print logs with diff between files : 

```bash
$ git log --stat
```

## Remote

### Common remote

Verbose format of remote: 
```bash
$ git remote -v
```

Add remote: 
```bash
$ git remote add [name] <url>
```
Default name is "origin"

### Other remote

Remove remote: 
```bash
$ git remote rm <name>
```

Rename remote: 
```bash
$ git remote rename <old> <new>
```

Show details: 
```bash
$ git remote show <remote1> [remote2] ...
```

```bash
$ git remote show origin
* remote origin
  Fetch URL: git@bitbucket.org:syxbyi/blogs.git
  Push  URL: git@bitbucket.org:syxbyi/blogs.git
  HEAD branch: master
  Remote branch:
    master tracked
  Local ref configured for 'git push':
    master pushes to master (local out of date)
```

## Branch
### Common fetch

List branches: 

```bash
$ git branch -a
$ git branch -r
```

Delete a branch: 
```bash
$ git branch -d <name>
```

## Checkout
### Common checkout

Create a branch and switch to it
```bash
$ git checkout -b <name>
```

## Merge
### Common merge

Merge a branch with this: 
```bash
$ git merge <name>
```

## Fetch
### Common fetch

Use to check others' work: 
```bash
$ git fetch <remote> [branch]
```
Fetched branch named "[remote]/[branch]"


## See also

[Git tutorial on github](https://github.com/geeeeeeeeek/git-recipes/wiki/2.4-%E6%A3%80%E6%9F%A5%E4%BB%93%E5%BA%93%E7%8A%B6%E6%80%81)

# Problem-solving

## 1: Host key verification failed

When: 

```bash
$ git clone git@github.com:xxxx/xxxx.git
```

And output:
```
Cloning into 'xxxx'...
The authenticity of host 'github.com (192.30.253.112)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? 
Host key verification failed.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

Try this:

```bash
$ ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts
```


# git常用命令:

## 基本命令
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
