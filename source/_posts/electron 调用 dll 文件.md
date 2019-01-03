---
title:      "electron 调用 dll 文件"
tags:
    - electron
---

# electron 调用 dll 文件

## 方案
1. 使用node-ffi
2. 使用C++编写node addon，通过LoadLibrary调用dll
3. 把dll的操作封装成一个c# exe，然后通过node原生child_process模块去调用子程序exe。node和子程序直接通信


## 使用node-ffi

### **什么是node-ffi**
   node-ffi是使用纯JavaScript加载和调用动态库的node addon，可以不写任何C++代码的情况下调用动态链接库的API 接口。
它本质上还是一个编译后的Node addon,node_modules/ffi/build/Release/ffi_bindings.node， ffi_bindings.node就是一个addon,ffi充当了nodejs和动态链接库之间的桥梁。

	*动态链接库后缀*  
	  'linux':  '.so'  
	  'linux2': '.so'  
	  'sunos':  '.so'  
	  'solaris':'.so'  
	  'freebsd':'.so'  
	  'openbsd':'.so'  
	  'darwin': '.dylib'  
	  'mac':    '.dylib'  
	  'win32':  '.dll'  

### **如何调用用node-ffi** 
     
    
		import ffi from 'ffi'
		import path from 'path'
	
		const libPath = path.join(__dirname, './add.dll')
		const lib = ffi.Library(libPath, {
		  'add': ['int', ['int', 'int']],
		})
		
		lib.add(3,1) // 4
		
		
### **调用前的工作**  

   ```
   npm install ffi
   ```		
 
  安装过程中会调用 ```node-gyp rebuild ```   编译node addon   
可能遇到的问题  

* node-gyp 没有安装
* 如果是windows  
   （1） python 没有安装 需要安装python2.7
    (2) python 环境变量没有配置或者配置不对  
    (3）NET Framework 4.5.1 没有
   （4） Visual C++编译工具 没有和node-gyp配置关联
   
   
  
 **electron中使用ffi**
 
 electron支持node原生模块，由于和官方的node使用不同的 V8 引擎，如果你想编译原生模块，则需要手动设置electron的headers的位置

**electron安装node原生模块**  
如下三种方法教你安装原生模块

1. 通过 npm 安装
只要设置一些系统环境变量，你就可以通过 npm 直接安装原生模块。
为 Electron 安装所有依赖项的一个例子:

```
# Electron 的版本。
export npm_config_target=1.2.3
# Electron 的系统架构, 值为 ia32 或者 x64。
export npm_config_arch=x64
export npm_config_target_arch=x64
# 下载 Electron 的 headers。
export npm_config_disturl=https://atom.io/download/electron
# 告诉 node-pre-gyp 是为 Electron 构建。
export npm_config_runtime=electron
# 告诉 node-pre-gyp 从源代码构建模块。
export npm_config_build_from_source=true
# 下载所有依赖，并缓存到 ~/.electron-gyp。
HOME=~/.electron-gyp npm install
```

2. 为 Electron 安装并重新编译模块
你可以也选择安装其他 Node 项目模块一样，然后用 electron-rebuild 包重建 Electron 模块 。 它可以识别当前 Electron 版本，帮你自动完成了下载 headers、编译原生模块等步骤。

一个下载 electron-rebuild 并重新编译的例子：

```
npm install --save-dev electron-rebuild

# 每次运行"npm install"时，也运行这条命令
./node_modules/.bin/electron-rebuild

# 在windows下如果上述命令遇到了问题，尝试这个：
.\node_modules\.bin\electron-rebuild.cmd
为 Electron 手动编译
```

3. 如果你是一个原生模块的开发人员，想在 Electron 中进行测试， 你可能要手动编译 Electron 模块。 你可以 使用 node-gyp 直接编译：

```
cd /path-to-module/
HOME=~/.electron-gyp node-gyp rebuild --target=1.2.3 --arch=x64 --dist-url=https://atom.io/download/electron
```

```HOME=~/.electron-gyp``` 设置去哪找开发时的 headers。 ```--target=1.2.3``` 设置了 Electron 的版本。``` --dist-url=...```设置了 Electron 的 headers 的下载地址。 ```--arch=x64``` 设置了该模块为适配64位操作系统而编译。



### node-ffi 使用详解


```
	import ffi from 'ffi'
	import path from 'path'
	
	const libPath = path.join(__dirname, './add.dll')
	const lib = ffi.Library(libPath, {
	  'add': ['int', ['int', 'int']],
	})
	
	lib.add(3,1) // 4
```

	
ffi.Library方法，第一个参数传入dll路径，第二参数JSON对象配置相关接口。  
key对应dll头文件中输出的接口，例如add()；  
value array配置参数类型，array[0]注册接口函数返回值类型，array[1]注册接口函数传入形参类型。

1、基础参数类型bool, char, short, int, long等。   
2、指针类型，需要引入ref模块，举例如下：

```
var ref = require('ref');
var intPointer = ref.refType('char');
var doublePointer = ref.refType('short');
var charPointer = ref.refType('int');
var stringPointer = ref.refType('long');
var boolPointer = ref.refType('bool');
```

### 常见错误

**Dynamic Linking Error: Win32 error 126**

这个错误有三种原因

1. 通常是传入的DLL路径错误，找不到Dll文件，推荐使用绝对路径。  
2. 如果是在x64的node/electron下引用32位的DLL，也会报这个错，反之亦然。要确保DLL要求的CPU架构和你的运行环境相同。
3. DLL还有引用其他DLL文件，但是找不到引用的DLL文件，可能是VC依赖库或者多个DLL之间存在依赖关系。


**Dynamic Linking Error: Win32 error 127**  
DLL中没有找到对应名称的函数，需要检查头文件定义的函数名是否与DLL调用时写的函数名是否相同。

### Path设置

如果你的DLL是多个而且存在相互调用问题，会出现Dynamic Linking Error: Win32 error 126错误3。  
这是由于默认的进程Path是二进制文件所在目录，即node.exe/electron.exe目录而不是DLL所在目录，导致找不到DLL同目录下的其他引用。可以通过如下方法解决：

```
//方法一， 调用winapi SetDllDirectoryA设置目录
const ffi = require('ffi')

const kernel32 = ffi.Library("kernel32", {
'SetDllDirectoryA': ["bool", ["string"]]
})
kernel32.SetDllDirectoryA("pathToAdd")

//方法二（推荐），设置Path环境环境
process.env.PATH = `${process.env.PATH}${path.delimiter}${pathToAdd}`
```

### 实际中遇到的坑 

1. 在mac上，node-ffi会给不是。dylib后缀的文件自动加上 .dylib 的后缀。 导致报找不到文件的错。  
2. 打包后在windows机器上跑，报错，node不是32位（系统是32位的）
3. electron相关的东西安装时下载卡卡卡


## 填坑历程
**关于坑3**  

1. .npmrc 文件中配置下载源


	```
	ELECTRON_MIRROR=http://npm.taobao.org/mirrors/electron/
	
	registry=https://registry.npm.taobao.org
	sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
	phantomjs_cdnurl=http://npm.taobao.org/mirrors/phantomjs
	```

2. electron-builder时 下载配置

	```
	 "build": {
	 
	    "electronDownload": {
	      "mirror": "http://npm.taobao.org/mirrors/electron/"
	    }
	  },
	```

**关于坑1，2**  
1. 手打编译node-ffi 文件匹配windows 32 位文件  
    结果：报错，node不是32位（系统是32位的）
2. 安装windows 32位虚拟机，在32位系统上打包  
   （配置一系列的编译环境）
   结果： 编译的时候报一堆v8引擎的错，看不懂    
3. 网上找electron-ffi 的例子源码，去虚拟机上跑
   结果： 竟然神奇的跑通了！！！  
4. 对比两个项目的差异，发现electron 版本不同，例子上1.7.11 
    ，工程项目2.0.11  
5. 对工程项目electron版本降级， success !!!    


		
		
	

