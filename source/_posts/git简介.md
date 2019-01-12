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

```
$ git config --global user.name "yourname"    
$ git config --global user.email "youremail"
```

**--global**配置全局文件，所有的项目都会默认使用这里配置的用户信息  
只要去掉 --global 只在当前项目配置


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
$ git config user.name
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
git status -s
git diff 
git add <file>
git commit -m "xxx"
```


## 基本命令加选项

```
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
git reset HEAD  // 取消已缓存的内容



