---
title: yeoman
date: 2018-11-21 23:28:17
tags:
---


# 设置开发环境
## 1.1 安装条件
安装yeoman之前，你需要先安装如下内容

* Nodejs v4 或者更高版本
* npm
* git

通过以下命令检查是否安装 Node 环境以及 npm 管理工具。

	$ node -v && npm -v

npm 默认随 Node 一起安装。有些 Node 版本可能安装的是旧版本的 npm，你可以通过以下命令更新 npm

	$ npm install -g npm@latest

通过以下命名检查是否安装git

	$ git --version

## 1.2 安装yeoman工具箱
如果已经安装了 node 环境，可以通过以下命令安装 Yeoman

	$ npm install -g yo

##1.3 确认安装
首先确认 Yeoman 是否正确安装

	$ yo --version

# 安装Yeoman生成器
在传统的 web开发中，你需要花大量时间为你的 webapp 设置模板代码、下载依赖包以及手动创建文件目录结构。Yeoman 的生成器会帮你搞定这一切

2.1安装生成器
你可以通过 npm 命令安装 Yeoman 生成器，目前可用的生成器超过了 3500 个，大多数都是开源社区贡献的。

通过以下命令安装 generator-webpack-simple-static

	$ npm install -g generator-webpack-simple-static
该命令将安装生成器所需的node包。

和使用 npm install 一样，你可以通过 Yeoman 的交互菜单搜索 generators。

运行 yo 然后选择 Install a generator 来搜索发布的生成器。

# 使用生成器搭建app
我们已经使用多次“脚手架”这个词，但是你可能还不知道它是什么意思。在 Yeoman的 语境中，脚手架材料表示通过一些配置为你的 webapp 生成文件。在这一步中，你会看到 Yeoman 如何为你喜欢的库及框架生成文件，以及使用如 webpack/babel/Sass 等一些额外的库的配置。

3.1 创建项目文件夹

	$ mkdir mytodo && cd mytodo
生成器生成的脚手架文件会放在这个文件夹中。

3.2 通过 Yeoman 菜单使用生成器
再次运行 yo

	$ yo
如果你已经安装了多个 generator，你需要从中选择一个。选中 generator-webpack-simple-static，按回车 enter 运行生成器。
