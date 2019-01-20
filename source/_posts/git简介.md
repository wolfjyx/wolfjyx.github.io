---
title:      "git 简介"
tags:
    - git
---

# git简介
Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。

# git配置
## 用户名和电子邮件配置

通常：

```
$ git config --global user.name "yourname"    
$ git config --global user.email "youremail"

$ ssh-keygen -t rsa -C "youremail@example.com"
```

**--system**配置全系统文件，文件位置/etc/gitconfig， 包含系统上每一个用户及他们仓库的通用配置  
**--global**配置当前用户全局文件，文件位置 ~/.gitconfig 或 ~/.config/git/config ，所有的项目都会默认使用这里配置的用户信息   
去掉**--global**，文件位置：.git/config 只在当前项目配置


## 文本编辑器配置
```
$ git config --global core.editor emacs
```

## 差异分析工具配置
```
git config --global merge.tool vimdiff
```
git支持 kdiff3，tkdiff，meld，xxdiff，emerge，vimdiff，gvimdiff，ecmerge，和 opendiff等工具

## 查看配置信息
查看全部配置

```
$ git config --list
```
查看单个配置(用户名）

```
$ git config <key>
```

# git 工作区、暂存区和版本库

* 工作区：本地环境
* 暂存区：英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）
* 版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

补图

# git 命令

## 基本，不解释

```
git init
git clone <repo><directory>
git status
git diff 
git add <file>
git commit -m "xxx"
git log
```


## 基本命令加选项

```
git status --short
git status -s  // 简短的结果输出
git diff // 尚未缓存的改动
git diff --cached // 查看已缓存的改动
git diff HEAD  查看已缓存的与未缓存的所有改动
git diff --stat 显示摘要而非整个diff
git commit -a  //  git add 并且 git commit 
```

## git rm 
从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除，然后提交

```
git rm <file>
git rm -f <file> // 如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f
git rm --cached <file> // 如果把文件从暂存区域移除，但仍然希望保留在当前工作目录中，换句话说，仅是从跟踪清单中删除，使用 --cached 选项即可
git rm –r * // 递归删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件
```
## git mv
git mv 命令用于移动或重命名一个文件、目录、软连接

```
git mv <filename>  <filename>
```

## git reset

```
git reset HEAD  // 取消已缓存的内容
```

## git log

    选项        |说明
-------------  | -------------
   -p          | 按补丁格式显示每个更新之间的差异。
--stat         | 显示每次更新的文件修改统计信息。
--shortstat    | 只显示 --stat 中最后的行数修改添加移除统计。
--name-only	  | 仅在提交信息后显示已修改的文件清单。
--name-status	  | 显示新增、修改、删除的文件清单。
--abbrev-commit | 仅显示 SHA-1 的前几个字符，而非所有的 40 个字符。
--relative-date | 使用较短的相对时间显示（比如，“2 weeks ago”）。
--graph			| 显示 ASCII 图形表示的分支合并历史。
--pretty			| 使用其他格式显示历史提交信息。可用的选项包括 oneline，short，full，fuller 和 format（后跟指定格式）。
-(n)				| 仅显示最近的 n 条提交
--since, --after | 仅显示指定时间之后的提交。
--until, --before | 仅显示指定时间之前的提交。
--author			| 仅显示指定作者相关的提交。
--committer     | 仅显示指定提交者相关的提交。
--grep 			| 仅显示含指定关键字的提交
-S					| 仅显示添加或移除了某个关键字的提交


```
git log -p -2 // 比较最近两次提交的差异
git log --stat // 每次提交的简略的统计信息
git log --pretty [online,short,full,fuller] //  指定使用不同于默认格式的方式展示提交历史
git log --pretty=format:"%h - %an, %ar : %s" // 定制要显示的记录格式

```

## git remote

```
git merge --no-ff -m "merge with no-ff" dev
```
禁用fast-forward合并模式

## git stash 

```
git stash // 储藏当前工作现场
git stash list // 查看
git stash apply // 只恢复储藏的内容
git stash drop // 删除stash内容
git stash pop // 恢复储藏的内容,并删除储藏
```



## git 撤销

```
 git commit --amend // 重新提交
 git reset HEAD <file> // 取消指定文件暂存
 git checkout -- <file> // 撤销指定文件修改
 git reset --hard commit_id  // HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令。
git reflog // 查看命令历史
```

HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，往上100个版本HEAD~100



## git 远程仓库

```
git remote add <shortname> <url>  // 添加远程仓库
git fetch [remote-name] // 同步远程仓库信息
git pull [remote-name] // 拉取远程仓库信息
git push [remote-name] [branch-name] // 把信息推送到远程仓库
git remote show [remote-name] // 查看远程仓库信息
git remote rename [old-name] [new-name] // 远程仓库重命名
git remote rm // 移除一个远程仓库
``` 

# git tag


```
git tag // 查看所有tag
git tag -l <n> // 查看n相关标签
git tag -a  <tag> // 创建附注标签
git tag <tag>  // 创建轻量标签
git tag -a <tag> <commit-hash> // 给历史提交打标签
git tag -d <tag> // 删除标签
git push origin :refs/tags/<tag> // 删除远程标签
git push origin [tagname] // 推送某次tag到远程
git push origin --tags // 推送所有标签
git checkout -b [branchname] [tagname] // 在特定的标签上创建一个新分支
```

## git 别名
常用

```
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

其他

```
git config --global alias.unstage 'reset HEAD --'  // 取消暂存文件
git config --global alias.last 'log -1 HEAD'  // 查看最后一次提交
```

## git branch

```
git branch <branch-name> // 创建分支
git branch // 查看分支
git branch -v // 查看每一个分支的最后一次提交
git branch --merged // 查看已合并分支
git branch --no-merged // 查看未合并分支
git branch -d <branch-name> // 删除分支
git branch -vv // 将所有的本地分支列出来并且包含更多的信息，如每一个分支正在跟踪哪个远程分支与本地分支是否是领先、落后
git fetch --all; git branch -vv  // 抓取所有的远程仓库, 统计最新的领先与落后数字
```

## git 远程分支

```
git push origin --delete <branch-name> 删除远程分支
```

## git 变基
使用 rebase 命令将提交到某一分支上的所有修改都移至另一分支上，

与合并的区别：  
变基是将一系列提交按照原有次序依次应用到另一分支上，
合并是把最终结果合在一起。

```
git rebase --onto master server client
```
取出 client 分支，找出处于 client 分支和 server 分支的共同祖先之后的修改，然后把它们在 master 分支上重放一遍

**不要对在你的仓库外有副本的分支执行变基** 


## git apply & git am

使用 apply 命令应用补丁
```git apply --check```检查补丁是否可以顺利应用

## rerere 
Rerere 是“重用已记录的冲突解决方案（reuse recorded resolution）”的意思——它是一种简化冲突解决的方法。 

```
 git config --global rerere.enabled true
  git rerere
 ```


