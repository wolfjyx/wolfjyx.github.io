---
title:      "freemark"
tags:
    - freemark 模板
---

# FreeMarker

## summary
  基于模板的，用来生成输出文本的通用工具  
  适用于MVC模式，分离思想   
  并非web的应用框架，只是框架中的一个组件，其引擎本身并不知道http协议或者servlet

## freemark 模板
  * `${...}` interpolations 插值 
  * `<#> </#>` tags 标签  （`<@> </@>` 自定义标签)
  * `<#--  -->` comments 注释
  * `<table></tabel>` directives 指令  
  
## 指令
 
### if指令
条件  
`<#if boolean><#else></#if>`

### list指令
循环  
`<#list Array as array></#list>`

### include指令
插入其他文件到当前模板  
`<#include ""/>`

### 处理不存在的变量
变量不存在时使用default代替  

`${...}!"default"`  

使用？？和if指令，变量不存在忽略代码段  

`<#if argument??></if>`

`argument1.argument2.argument3!0`  
若argument1或argument2不存在，则模板处理会以“未定义变量”错误停止  
通过`（argument1.argument2.argument3）!0` 方式防止这种错误

### 用户自定义指令
如果能够实现，用自定义指令而不用函数/方法。  
输出（返回值）的是标记（HTML,XML 等）。  
主要原因是函数的返回结果可以自动进行 XML 转义  
（这是因为${…}的特性），  
而用户自定义指令的输出则不是  
（这是
因为<@...>的特性所致，它的输出假定为是标记，因此就不再转义）。

### 转义
**特殊字符** 原生字符 `${r"${foo}"}`



