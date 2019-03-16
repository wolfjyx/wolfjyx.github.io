title:      "JOSN WEB TOKEN"
tags:
---

## 定义
[JSON Web Token（JWT)]( jwt.io Debugger)是一种开放标准 [RFC7519](https://tools.ietf.org/html/rfc7519)。   
它定义了一种紧凑的、自包含的方式，将信息作为JSON对象在各方之间安全地传输。  
由于使用了数字签名，该信息是可以验证和信任的。
JWT可以使用密码（使用HMAC算法）或使用RSA或ECDSA的公钥/私钥对进行签名。  
总之，JSON Web Token（JWT）是一个非常轻巧的规范。这个规范允许我们使用JWT在用户和服务器之间传递安全可靠的信息。



## 结构
在其紧凑的形式中，JWT 由三个部分组成，由点（.）分隔，分别是：

* Header 头部
* Payload 载荷
* Signature 签名

因此，JWT通常如下所示。

```
xxxxx.yyyyy.zzzzz
```

### 头部 (header)

头通常由两部分组成：令牌的类型（JWT）和正在使用的签名算法（如HMAC SHA256或RSA）。

```
{
  "alg": "HS256",
  "typ": "JWT"
}
```

将JSON转为base64url编码，以形成JWT的第一部分

### 载荷（payload)
载荷包含声明。声明是关于实体（通常是用户）和附加数据的语句。  
声明有三种类型：注册声明、公开声明和私有声明

**注册声明**  
这是一组预定义的声明，这些声明是建议但不必需的  
该声明提供一组有用的、可交换操作的声明

* iss:(Issuer)  该JWT的签发者  
* sub:(Subject) 该JWT所面向的用户  
* aud: (Audience)接收该JWT的一方  
* exp(expires): 什么时候过期，这里是一个Unix时间戳  
* nbf (Not Before) 该JWT到什么时间有效  
* iat(issued at): 在什么时候签发的  
* jti(JWT ID)：该JWT唯一标识  

**公开声明**   
这些可以由使用JWT的人员随意定义。但是为了避免冲突，应该是在 [IANA JSON Web Token Registry](https://www.iana.org/assignments/jwt/jwt.xhtml)中定义的  
或者将它们定义为包含防冲突命名空间的URI。

**私有声明**
自定义声明，用来在各方间共享信息，区别于注册声明和公开声明 

这是载荷的一个实例

```
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```
将JSON转为base64url编码，以形成JWT的第二部分

### 签名 (Signature)
签名部分，包含 编码过的头部、编码过的载荷、密码、头部中指定的算法，并对这些此进行签名计算。

例如，如果要使用hmac sha256算法，将按以下方式创建签名：

```
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

签名用于验证消息是否在过程中发生了更改，对于使用私钥签名的令牌，它还可以验证JWT的发送者是它所说的人。

## jWT如何工作

在身份验证中，当用户使用其凭据成功登录时，将返回JWT。因为令牌是凭证，所以必须非常小心地防止安全问题。一般来说，您不应该将令牌保留超过所需的时间。

每当用户想要访问受保护的路由或资源时，用户代理应该使用承载模式发送JWT，通常是在授权头中。标题的内容应如下所示：

```
Authorization: Bearer <token>
```

在某些情况下，这可以是无状态授权机制。服务器的受保护路由将检查授权头中是否存在有效的JWT，如果存在，则允许用户访问受保护的资源。如果JWT包含必要的数据，那么查询数据库进行某些操作的需求可能会减少，尽管情况并非总是如此。

如果token设置在Authorization，Cross-Origin Resource Sharing (CORS) 将不再是问题，因为这不适用cookie

如何获取和使用JWT来访问API或资源：

1. 应用程序或客户端向授权服务器请求授权。这是通过一个不同的授权流执行的。例如，典型的[ OpenID Connect](https://openid.net/connect/)兼容Web应用程序将使用[authorization code flow](https://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth)通过 /oauth/authorize端点。  
2. 授予授权后，授权服务器将向应用程序返回访问令牌。  
3. 应用程序使用访问令牌访问受保护的资源（如API）。 


ps: 对于签名的令牌，令牌中包含的所有信息都将向用户或其他方公开，即无法更改它。这意味着不应该将秘密信息放在令牌中。

## jwt优势
1. 传输数据量小
2. 安全方面，SWT只能使用HMAC算法由共享机密对称签名。但是，JWT和SAML令牌可以使用X.509证书形式的公钥/私钥对进行签名。与简单的JSON签名相比，用XML数字签名来签名XML而不引入模糊的安全漏洞是非常困难的。 
3. JSON解析器在大多数编程语言中很常见，因为它们直接映射到对象。相反，XML没有一个自然的文档到对象的映射。这使得使用JWT比使用SAML断言更容易。


## 适用场景
* 用于向Web应用传递一些非敏感信息。例如完成加好友、下订单的操作等等。
* 用于设计用户认证和授权系统。
* 实现Web应用的单点登录。