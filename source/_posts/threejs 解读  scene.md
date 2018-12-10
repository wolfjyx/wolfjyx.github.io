title:      "threejs 解读  scene"
tags:
    - js threejs
---
# Scene
## 概念
scene用来创建场景

## 使用:
创建一个scene对象：
```
Scence()
```

## 属性

### fog
fog实例，定义场景中的雾状背景。默认是null

### overrideMaterial
如果不为null,它将使用其材质强制覆盖场景中所有对象。默认为null

### autoUpdate
如果是ture,则每一帧自动检测矩阵更新.如果false,则需要手动维护矩阵更新。默认为true

### background
如果不为null，则设置渲染场景时使用的背景，并始终先渲染。 可以设置为**Color**，**Texture**或**CubeTexture**。 默认为null

## 方法
### toJSON
以JSON格式返回场景数据




# Fog
## 概念
此类包含定义线性雾的参数，即密度随着距离的增加呈线性增长

## 使用
创建Fog对象：
```
Fog( color : Integer, near : Float, far : Float )
```

color参数被传递给**Color**来设置颜色属性，color可以是一个十六进制整数或CSS样式的字符串

# 属性
### name
对象的可选名称（不必是唯一的),默认值为空字符串

### color
雾的颜色，例如：如果设置为黑色，远处的物体将被渲染为黑色

### near
开始施雾的最小距离。距离当前相机小于near单位的对象，将不会受到雾的影响。默认为1

### far
结束施雾的最大距离。距离当前相机大于far单位的对象，将不会受到雾的影响。默认为1000

# 方法
### clone
返回具有与此雾有相同的参数的新雾实例


### toJSON
以JSON格式返回线性雾数据


# FogExp2
## 概念
此类包含定义指数雾的参数，即密度随着距离的增加呈指数增长

## 使用
创建FogExp2对象：
```
FogExp2( color : Integer, density : Float )
````

color参数被传递给**Color**来设置颜色属性，color可以是一个十六进制整数或CSS样式的字符串

## 属性
## name
对象的可选名称（不必是唯一的),默认值为空字符串

## color
雾的颜色，例如：如果设置为黑色，远处的物体将被渲染为黑色

## density
定义雾密度增加的速度，默认0.00025

## 方法
### clone
返回具有与此雾有相同的参数的新雾实例


### toJSON
以JSON格式返回线性雾数据

