title:      "javascript & ECMAScript & es"
tags:
    - javascript
---
# JavaScript & ECMAScript & ES2015... & ES6...

## JavaScript	
JavaScript一种动态类型、弱类型、基于原型的客户端脚本语言，用来给HTML网页增加动态功能

JavaScript由三部分组成  
1. ECMAScript  
2. DOM  
3. BOM

## ECMAScript
一个由 ECMA International 进行标准化，TC39 委员会进行监督的语言。通常用于指代标准本身


**ECMA**  
Ecma国际（Ecma International）是一家国际性会员制度的信息和电信标准组织。1994年之前，名为欧洲计算机制造商协会（European Computer Manufacturers Association）。因为计算机的国际化，组织的标准牵涉到很多其他国家，因此组织决定改名表明其国际性。现名称已不属于首字母缩略字。

Ecma国际是一家和企业密切相连的组织，所以 Ecma国际制定的规范都是由各类企业来做主要的制定和推广

**TC39**  
在ECMA国际，每个标准都会有一个 TC 来负责，而一个 TC 中可能会有不同的 TG 来负责不同的工作。而负责 ECMA262，也就是我们所说的 ECMAScript 的就是 TC39（以前叫 TC39-TG1）。  
***TC（Technical Committees）***  
***TG（Task Groups）***



要讲清ECMAScript，回顾历史。  
1996 年 11 月，JavaScript 的创造者 Netscape 公司，决定将 JavaScript 提交给标准化组织 ECMA，希望这种语言能够成为国际标准。次年，ECMA 发布 262 号标准文件（ECMA-262）的第一版，规定了浏览器脚本语言的标准，并将这种语言称为 ECMAScript，这个版本就是 1.0 版。  
该标准从一开始就是针对 JavaScript 语言制定的，但是之所以不叫 JavaScript，有两个原因。一是商标，Java 是 Sun 公司的商标，根据授权协议，只有 Netscape 公司可以合法地使用 JavaScript 这个名字，且 JavaScript 本身也已经被 Netscape 公司注册为商标。二是想体现这门语言的制定者是 ECMA，不是 Netscape，这样有利于保证这门语言的开放性和中立性。

**ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现**

ECMAScript 作为一门脚本程序设计语言标准，并不只有 javascript 这一种实现，它也有很多的方言实现。比如有下面这些语言：

JavaScript

Ejscript

JScript .NET

ActionScript

DMDScript

CriScript

InScript



## ES2015...
**ES2015**  
**ECMAScript 2015**  
ECMAScript 的第六版修订，于 2015 年完成标准化。这个标准被部分实现于大部分现代浏览器。  

**ECMAScript 2016**    
第七版 ECMAScript 修订，只加了Array.prototype.includes、Exponentiation Operator(求冥运算)

**ECMAScript 2017**   
第八版 ECMAScript 修订  
新增  
Object.values/Object.entries  
字符串填充    padStart()和padEnd()  
Object.getOwnPropertyDescriptor
尾随逗号  
异步函数async  
共享内存和原子操作  

**ECMAScript 2018**   
异步迭代  
Promise.finally()  
Rest/Spread 属性: ES2018为对象解构提供了和数组一样的Rest参数（）和展开操作符   
正则表达式命名捕获组（Regular Expression Named Capture Groups）  
正则表达式反向断言（lookbehind）
正则表达式dotAll模式  
正则表达式 Unicode 转义  
非转义序列的模板字符串

**ECMAScript Proposals**   
被考虑加入未来版本 ECMAScript标准的特性与语法提案，他们需要经历五个阶段：

stage| 名称  | 描述
------ | ---- | -------------
Stage 0 | strawman（稻草人） | 任何人都可以提交pull request到[GitHub - tc39/ecma262: Status, process, and documents for ECMA262](https://github.com/tc39/ecma262)
Stage 1 | Proposal（提议） | TC39制定成员作为 champion，TC39审阅通过，有实现的 Demo 或者 Polyfill初步描写标准的语义语法算法复杂度解决的问题等
Stage 2 | Draft（草案）| 有两个或两个以上的实现（包括babel这类的转译实现）使用正式的语言描述该语法，api等
Stage 3 | Candidate（候选） | 至少2个实现，可以为实验性实现，ECMAScript spec editor 通过审核，TC39 review 通过，文本编写完成
Stage 4 | Finished （完成）| 编写 test 262 测试用例，通过两个实现该特性的内核测试，ECMAScript spec editor 通过审核，开发者表示支持和认可


对于有些人来说，前端的更新总是很突兀，很让人迷茫。

但是其实不是的。变化总是一点一点发生的。

[GitHub - tc39/proposals: Tracking ECMAScript Proposals](https://link.zhihu.com/?target=https://github.com/tc39/proposals)

我们可以在 TC39 的 Github 仓库中找到完成了，废弃的，以及正在进行中的提案。

多去关注这些东西，对于很多新事物的到来，我们也就不会有多惊讶了。

**其他ECMA标准**  
和 ECMAScript 有关的标准有 ECMA262，ECMA290，ECMA327，ECMA357，ECMA402，ECMA404，ECMA414等等。

其中290，327，357等等没有推广开来，被废弃。

ECMA 262 是语言规范本身。

ECMA 402 则是制定一些基于 ECMAScript 5 或者之后版本的一些国际化 API 标准。

ECMA 404 是 JSON 规范。

ECMA 414 则规定了哪些规范是和 ECMAScript 有关的。目前内部就包含了 262，402和404。



## ES6...
ES   | ECMAScript
---- | -------------
 ES6 | ECMAScript 2015
 ES7 | ECMAScript 2016
 ES8 | ECMAScript 2017
 ES9 | ECMAScript 2018
 
 ES1：1997 年 6 月  ——    
 ES2：1998 年 6 月  ——   
 ES3：1999 年 12月  ——     
 ES4： 2007 年 10月  **未通过**  ——   
 ES5： 2009年12月  ——   
 ES5.1  2011年6月  ——

**ES4&ES3.1**  
在制定ES4的时候，是分成了两个工作组同时工作的。

一边是以 Adobe, Mozilla, Opera 和 Google为主的 ECMAScript 4 工作组。

一边是以 Microsoft 和 Yahoo 为主的 ECMAScript 3.1 工作组。

ECMAScript 4 的很多主张比较激进，改动较大。而 ECMAScript 3.1 则主张小幅更新

最终经过 TC39 的会议，决定将一部分不那么激进的改动保留发布为 ECMAScript 3.1，然后将一部分比较激进的部分放置到 ES.NEXT 中，命名为 Harmony（和谐），留待以后再进行商榷。接下来，ECMAScript  3.1 变成了 ECMAScript 5，而 ES.NEXT 中的那些特性，则有着相当一部分被ECMAScript 6，也就是 ECMAScript 2015 所吸收了。所以说虽然 ECMAScript 4 被废弃了，但是它终究还是通过另一种方式活了下来。



