title:      "threejs 解读  geometry"
tags:
    - js threejs
---

# BoxGeometry

## 概念
盒子几何模型，长、宽、高可不等

## 使用
```
BoxGeometry(width : Float, height : Float, depth : Float, widthSegments : Integer, heightSegments : Integer, depthSegments : Integer)
```
width - x轴上的宽度，默认为1  
height - y轴上的高度，默认为1  
depth - z轴上的深度，默认为1  
widthSegments — 可选参数. 沿宽度面的分割面数量. 默认值为1  
heightSegments — 可选参数. 沿高度面的分割面数量. 默认值为1  
depthSegments — 可选参数. 沿深度面的分割面数量. 默认值为1  

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何

# BoxBufferGeometry
##概念
 BoxGeometry 部分的 BufferGeometry 
 
## 使用
```
BoxBufferGeometry(width : Float, height : Float, depth : Float, widthSegments : Integer, heightSegments : Integer, depthSegments : Integer)
```

width - x轴上的宽度，默认为1  
height - y轴上的高度，默认为1  
depth - z轴上的深度，默认为1  
widthSegments — 可选参数. 沿宽度面的分割面数量. 默认值为1  
heightSegments — 可选参数. 沿高度面的分割面数量. 默认值为1  
depthSegments — 可选参数. 沿深度面的分割面数量. 默认值为1  
## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何


#CircleGeometry
##概念
CircleGeometry是一个简单的欧氏几何形。它是众多三角形面围绕一个中心点并延伸到给定的半径范围而组成。它是用一个开始角度和一个给定的中心角度逆时针建立。它可以用来创建规则的多边形模型，其中分割面的数量决定的面的数量。


##使用
```
CircleGeometry(radius : Float, segments : Integer, thetaStart : Float, thetaLength : Float)
```
radius — 圆的半径, 默认为1.
segments — 分割面数量 (三角形), 最小值为3, 默认值 = 8.
thetaStart — 第一个分割面的开始角度, 默认值为0 (3点钟方向).
thetaLength — 圆形扇形的圆心角通常称为 θ。默认为2 * Pi

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何



#CircleBufferGeometry
##概念
 CircleGeometry 部分的 BufferGeometry 

##使用
```
CircleBufferGeometry(radius : Float, segments : Integer, thetaStart : Float, thetaLength : Float)
```
radius — 圆的半径, 默认为1.
segments — 分割面数量 (三角形), 最小值为3, 默认值 = 8.
thetaStart — 第一个分割面的开始角度, 默认值为0 (3点钟方向).
thetaLength — 圆形扇形的圆心角通常称为 θ。默认为2 * Pi

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# ConeGeometry
## 概念
用于生成锥形几何的类

##使用
```
ConeGeometry(radius : Float, height : Float, radialSegments : Integer, heightSegments : Integer, openEnded : Boolean, thetaStart : Float, thetaLength : Float)
```
adius — 锥底半径. 默认值为20  
height — 锥体高度. 默认值为100  
radiusSegments — 围绕圆锥周长的分割面数量. 默认值为8  
heightSegments — 沿圆锥高度的分割面数量. 默认值为1  
openEnded — 指示锥底是否打开, 默认值为false
thetaStart — 第一个分割面的开始角度, 默认值 = 0 (3点钟方向)  
thetaLength — 圆形扇形的圆心角通常称为θ。默认为2 * Pi.



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ConeBufferGeometry
## 概念
ConeGeometry 部分的 BufferGeometry 

##使用
```
ConeGeometry(radius : Float, height : Float, radialSegments : Integer, heightSegments : Integer, openEnded : Boolean, thetaStart : Float, thetaLength : Float)
```
adius — 锥底半径. 默认值为20  
height — 锥体高度. 默认值为100  
radiusSegments — 围绕圆锥周长的分割面数量. 默认值为8  
heightSegments — 沿圆锥高度的分割面数量. 默认值为1  
openEnded — 指示锥底是否打开, 默认值为false
thetaStart — 第一个分割面的开始角度, 默认值 = 0 (3点钟方向)  
thetaLength — 圆形扇形的圆心角通常称为θ。默认为2 * Pi.



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# CylinderGeometry
## 概念
用于生成圆柱几何的类

## 使用
```
CylinderGeometry(radiusTop : Float, radiusBottom : Float, height : Float, radialSegments : Integer, heightSegments : Integer, openEnded : Boolean, thetaStart : Float, thetaLength : Float)
```

radiusTop — 圆柱体顶端半径. 默认值为20.  
radiusBottom — 圆柱体底端半径. 默认值为20.  
height — 圆柱体高度. 默认值为100.  
radiusSegments — 围绕圆柱体周长的分割面数量. 默认值为8.  
heightSegments — 沿圆柱体高度的分割面数量. 默认值为1.  
openEnded — 指示圆柱体两端是否打开. 默认值为false  
thetaStart — 第一个分割面的开始角度, 默认值 = 0 (3点钟方向).  
thetaLength — 圆形扇形的圆心角通常称为θ。默认为2 * Pi


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# CylinderBufferGeometry
## 概念
CylinderGeometry 部分的 BufferGeometry 

## 使用
```
CylinderGeometry(radiusTop : Float, radiusBottom : Float, height : Float, radialSegments : Integer, heightSegments : Integer, openEnded : Boolean, thetaStart : Float, thetaLength : Float)
```

radiusTop — 圆柱体顶端半径. 默认值为20.  
radiusBottom — 圆柱体底端半径. 默认值为20.  
height — 圆柱体高度. 默认值为100.  
radiusSegments — 围绕圆柱体周长的分割面数量. 默认值为8.  
heightSegments — 沿圆柱体高度的分割面数量. 默认值为1.  
openEnded — 指示圆柱体两端是否打开. 默认值为false  
thetaStart — 第一个分割面的开始角度, 默认值 = 0 (3点钟方向).  
thetaLength — 圆形扇形的圆心角通常称为θ。默认为2 * Pi


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# DodecahedronGeometry

## 概念
用于生成十二面体几何的类

## 使用
```
DodecahedronGeometry(radius : Float, detail : Integer)
```

radius — 十二面体的半径. 默认值为1.   
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个十二面体  

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  




# DodecahedBufferronGeometry

## 概念
DodecahedonGeometry 部分的 BufferGeometry 

## 使用
```
DodecahedronGeometry(radius : Float, detail : Integer)
```

radius — 十二面体的半径. 默认值为1.   
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个十二面体  

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ExtrudeGeometry

## 概念
这可以用作辅助对象来查看Geometry对象的边缘

## 使用
```
EdgesGeometry( geometry : Geometry, thresholdAngle : Integer )
```
geometry - 任何几何对象   
thresholdAngle - 仅当相邻面的面法线之间的角度（以度为单位）超过此值时，才会渲染边。 默认为1度


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ExtrudeGeometry

## 概念
从路径形状创建拉伸几何体

## 使用
```
ExtrudeGeometry(shapes : Array, options : Object)
```

shapes — 形状或形状数组  
options — 包括下面这些参数的对象.  

* curveSegments — int. 曲线上点的个数  
* steps — int. 用于细分拉伸的样条段数量
* depth — int. 拉伸形状的深度
* bevelEnabled — bool. 打开斜面
* bevelThickness — float. 在原来的形状里面弄多深的斜面
* bevelSize — float. 斜面离形状轮廓的距离
* bevelSegments — int. 斜面层的数量
* extrudePath — THREE.CurvePath. 沿3D样条路径拉伸形状
* UVGenerator — Object. 提供UV生成器各功能的对象

这个对象将一个2D图形拉伸为一个3D几何体.  
在使用此几何体创建网格时，如果您希望将单独的材质用于其面和其拉伸边，则可以使用一组材质。 第一种材料将涂在形状面; 第二种材料将应用于侧面



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ExtrudeBufferGeometry

## 概念
从路径形状创建拉伸几何体

## 使用
```
ExtrudeBufferGeometry(shapes : Array, options : Object)
```

shapes — 形状或形状数组  
options — 包括下面这些参数的对象.  

* curveSegments — int. 曲线上点的个数  
* steps — int. 用于细分拉伸的样条段数量
* depth — int. 拉伸形状的深度
* bevelEnabled — bool. 打开斜面
* bevelThickness — float. 在原来的形状里面弄多深的斜面
* bevelSize — float. 斜面离形状轮廓的距离
* bevelSegments — int. 斜面层的数量
* extrudePath — THREE.CurvePath. 沿3D样条路径拉伸形状
* UVGenerator — Object. 提供UV生成器各功能的对象

这个对象将一个2D图形拉伸为一个3D几何体.  
在使用此几何体创建网格时，如果您希望将单独的材质用于其面和其拉伸边，则可以使用一组材质。 第一种材料将涂在形状面; 第二种材料将应用于侧面



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# IcosahedronGeometry

## 概念
用来创建二十面体几何模型的类

## 使用
```
IcosahedronGeometry(radius : Float, detail : Integer)
```

radius — 默认值为1. 
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个二十面体. 当值大于1时它就成了一个球体.

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# IcosahedronBufferGeometry

## 概念
用来创建二十面体几何模型的类

## 使用
```
IcosahedronBufferGeometry(radius : Float, detail : Integer)
```

radius — 默认值为1. 
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个二十面体. 当值大于1时它就成了一个球体.

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# LatheGeometry
## 概念
创建具有轴对称性的网格，如花瓶。 车床绕Y轴旋转。

## 使用

```
LatheGeometry(points : Array, segments : Integer, phiStart : Float, phiLength : Float)
```

points — Vector2s数组. X轴上每个点都必须大于0.  
segments — 生成圆周段的数目. 默认值为12.  
phiStart — 起始角度的弧度值. 默认值为0.  
phiLength — 弧度范围在0到2PI间的，2PI是闭合车床, 小于2PI的是部分。默认值为2PI.



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# LatheBufferGeometry
## 概念
创建具有轴对称性的网格，如花瓶。 车床绕Y轴旋转。

## 使用

```
LatheBufferGeometry(points : Array, segments : Integer, phiStart : Float, phiLength : Float)
```

points — Vector2s数组. X轴上每个点都必须大于0.  
segments — 生成圆周段的数目. 默认值为12.  
phiStart — 起始角度的弧度值. 默认值为0.  
phiLength — 弧度范围在0到2PI间的，2PI是闭合车床, 小于2PI的是部分。默认值为2PI.



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  



# OctahedBufferGeometry

## 概念
用来创建八面体几何模型的类

## 使用
```
OctahedGeometry(radius : Float, detail : Integer)
```

radius — 默认值为1. 
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个八面体.

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# OctahedronBufferGeometry

## 概念
用来创建八面体几何模型的类

## 使用
```
OctahedBufferGeometry(radius : Float, detail : Integer)
```

radius — 默认值为1. 
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个八面体.

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ParametricGeometry

## 概念
生成代表参数化曲面的几何模型

## 使用
```
ParametricGeometry(func : Function, slices : Integer, stacks : Integer)
```

func — 一个函数，接收介于0到1之间的 u 和 v 值，并返回一个 Vector3  
slices — 用于参数化函数的切片数量   
stacks — 用于参数化函数的堆栈数量  

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ParametricBufferGeometry

## 概念
生成代表参数化曲面的几何模型

## 使用
```
ParametricBufferGeometry(func : Function, slices : Integer, stacks : Integer)
```

func — 一个函数，接收介于0到1之间的 u 和 v 值，并返回一个 Vector3  
slices — 用于参数化函数的切片数量   
stacks — 用于参数化函数的堆栈数量  

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# PlaneGeometry
## 概念
用来生成平面几何模型的类


## 使用
```
PlaneGeometry(width : Float, height : Float, widthSegments : Integer, heightSegments : Integer)
```

width — 沿X轴宽度, 默认为1.  
height — 沿Y轴高度，默认为1.  
widthSegments — 可选参数，x方向的分段数，缺省为1  
heightSegments — 可选参数，y方向的分段数，缺省为1 


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# PlaneBufferGeometry
## 概念
用来生成平面几何模型的类


## 使用
```
PlaneBufferGeometry(width : Float, height : Float, widthSegments : Integer, heightSegments : Integer)
```

width — 沿X轴宽度, 默认为1.  
height — 沿Y轴高度，默认为1.  
widthSegments — 可选参数，x方向的分段数，缺省为1  
heightSegments — 可选参数，y方向的分段数，缺省为1 


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# PolyhedronGeometry
## 概念
多面体是由多个平面形成的三维几何体,它将取一个顶点数组并将它们投射到一个球体上，然后将它们划分成所需的期望细节层面

## 使用
```
PolyhedronGeometry(vertices : Array, indices : Array, radius : Float, detail : Integer)
```

vertices — Array 以 [1,1,1, -1,-1,-1, ... ] 这种形式出现的点的数组    
faces — Array 以 [0,1,2, 2,3,0, ... ] 这种形式出现的构成各个面的指数数组   
radius — Float - 最终形状的半径    
detail — Integer - 把几何模型细分成多少层. 层越多形状越光滑.  


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# PolyhedronBufferGeometry
## 概念
多面体是由多个平面形成的三维几何体,它将取一个顶点数组并将它们投射到一个球体上，然后将它们划分成所需的期望细节层面

## 使用
```
PolyhedronBufferGeometry(vertices : Array, indices : Array, radius : Float, detail : Integer)
```

vertices — Array 以 [1,1,1, -1,-1,-1, ... ] 这种形式出现的点的数组    
faces — Array 以 [0,1,2, 2,3,0, ... ] 这种形式出现的构成各个面的指数数组   
radius — Float - 最终形状的半径    
detail — Integer - 把几何模型细分成多少层. 层越多形状越光滑.  


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# RingGeometry 
## 概念
用于生成二维环几何的类

## 使用
```
RingGeometry(innerRadius : Float, outerRadius : Float, thetaSegments : Integer, phiSegments : Integer, thetaStart : Float, thetaLength : Float)
```

innerRadius — 默认值为0.5.
outerRadius — 默认值为1. 
thetaSegments — 分割面数量. 更高的值意味着更加的圆滑. 最小值为3. 默认值为8. 
phiSegments — 最小值为1. 默认值为8.
thetaStart — 开始角度. 默认值为0. 
thetaLength — 圆心角. 默认值为Math.PI * 2.

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# RingBufferGeometry 
## 概念
用于生成二维环几何的类

## 使用
```
RingBufferGeometry(innerRadius : Float, outerRadius : Float, thetaSegments : Integer, phiSegments : Integer, thetaStart : Float, thetaLength : Float)
```

innerRadius — 默认值为0.5.
outerRadius — 默认值为1. 
thetaSegments — 分割面数量. 更高的值意味着更加的圆滑. 最小值为3. 默认值为8. 
phiSegments — 最小值为1. 默认值为8.
thetaStart — 开始角度. 默认值为0. 
thetaLength — 圆心角. 默认值为Math.PI * 2.

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ShapeGeometry 
## 概念
从一个或多个路径形状创建单面多边形几何

## 使用
```
ShapeGeometry(shapes : Array, curveSegments : Integer)
```
shape - 形状数组或单个形状  
curveSegments - 整数 - 每个形状的段数。 默认值为12   

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# ShapeBufferGeometry 
## 概念
从一个或多个路径形状创建单面多边形几何

## 使用
```
ShapeBufferGeometry(shapes : Array, curveSegments : Integer)
```
shape - 形状数组或单个形状  
curveSegments - 整数 - 每个形状的段数。 默认值为12   

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# SphereGeometry 
## 概念
用于生成球体几何的类

## 使用
```
SphereGeometry(radius : Float, widthSegments : Integer, heightSegments : Integer, phiStart : Float, phiLength : Float, thetaStart : Float, thetaLength : Float)
```

radius — 球体半径. 默认值为50  
widthSegments — 水平分割面的数量. 最小值为3, 默认值为8  
heightSegments — 垂直分割面的数量. 最小值为2, 默认值为6  
phiStart — 指定水平起始角度. 默认值为0  
phiLength — 指定水平扫描角度大小. 默认值为 Math.PI * 2  
thetaStart — 指定垂直起始角度. 默认值为0  
thetaLength — 指定垂直扫描角度大小. 默认值为Math.PI  

几何模型是通过扫描和计算绕Y轴（水平扫描）和Z轴（垂直扫描）的顶点创建而成。因此，不完整的球（类似于'sphere slices'）可以通过对phistart，philength，thetastart和thetalength使用不同的值来创建

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# SphereBufferGeometry 
## 概念
用于生成球体几何的类

## 使用
```
SphereBufferGeometry(radius : Float, widthSegments : Integer, heightSegments : Integer, phiStart : Float, phiLength : Float, thetaStart : Float, thetaLength : Float)
```

radius — 球体半径. 默认值为50  
widthSegments — 水平分割面的数量. 最小值为3, 默认值为8  
heightSegments — 垂直分割面的数量. 最小值为2, 默认值为6  
phiStart — 指定水平起始角度. 默认值为0  
phiLength — 指定水平扫描角度大小. 默认值为 Math.PI * 2  
thetaStart — 指定垂直起始角度. 默认值为0  
thetaLength — 指定垂直扫描角度大小. 默认值为Math.PI  

几何模型是通过扫描和计算绕Y轴（水平扫描）和Z轴（垂直扫描）的顶点创建而成。因此，不完整的球（类似于'sphere slices'）可以通过对phistart，philength，thetastart和thetalength使用不同的值来创建

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TetrahedronGeometry
## 概念
用于生成四面体几何的类

## 使用
```
TetrahedronGeometry(radius : Float, detail : Integer)
```

radius — 四面体半径. 默认值为1.    
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个四面体.


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# TetrahedronBufferGeometry
## 概念
用于生成四面体几何的类

## 使用
```
TetrahedronBufferGeometry(radius : Float, detail : Integer)
```

radius — 四面体半径. 默认值为1.    
detail — 默认值为0. 设置为大于0的值将添加顶点使之不再是一个四面体.


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TextGeometry
## 概念
用于将文本生成为单个几何的类。 它是文本和传入的属性对象创建的

## 使用
```
TextGeometry(text : String, parameters : Object)
```
text — 要显示的文字   
parameters — 包含下面这些参数的对象  

* font — THREE.Font. 字体实例.
* size — Float. 文字大小， 默认为100.
* height — Float. 文字厚度. 默认值为50.   
* curveSegments — Integer. 曲线上点的数量. 默认值为12.
* bevelEnabled — Boolean. 是否打开斜面. 默认值为False.
* bevelThickness — Float. 文本斜面的深度. 默认值为10.
* bevelSize — Float. 斜面离轮廓的距离. 默认值为8.
* bevelSegments - Integer. 斜角段数. 默认值为3.
* 
## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TextBufferGeometry
## 概念
用于将文本生成为单个几何的类。 它是文本和传入的属性对象创建的

## 使用
```
TextBufferGeometry(text : String, parameters : Object)
```
text — 要显示的文字   
parameters — 包含下面这些参数的对象  

* font — THREE.Font. 字体实例.
* size — Float. 文字大小， 默认为100.
* height — Float. 文字厚度. 默认值为50.   
* curveSegments — Integer. 曲线上点的数量. 默认值为12.
* bevelEnabled — Boolean. 是否打开斜面. 默认值为False.
* bevelThickness — Float. 文本斜面的深度. 默认值为10.
* bevelSize — Float. 斜面离轮廓的距离. 默认值为8.
* bevelSegments - Integer. 斜角段数. 默认值为3.

## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TorusGeometry
## 概念
用于生成圆环几何的类

## 使用
```
TorusGeometry(radius : Float, tube : Float, radialSegments : Integer, tubularSegments : Integer, arc : Float)
```

radius — 半径, 默认值为1.   
tube — 管道直径. 默认值为 0.4.   
radialSegments — 默认值为8   
tubularSegments — 默认值为6.     
arc — 圆心角. 默认值为Math.PI * 2.  



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TorusBufferGeometry
## 概念
用于生成圆环几何的类

## 使用
```
TorusBufferGeometry(radius : Float, tube : Float, radialSegments : Integer, tubularSegments : Integer, arc : Float)
```

radius — 半径, 默认值为1.   
tube — 管道直径. 默认值为 0.4.   
radialSegments — 默认值为8   
tubularSegments — 默认值为6.     
arc — 圆心角. 默认值为Math.PI * 2.  



## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TorusKnotGeometry
## 概念

创建圆环结，其特定形状由一对互质整数p和q定义。 如果p和q不是互质的，则结果将是环面链接。

## 使用
```
TorusKnotGeometry(radius : Float, tube : Float, tubularSegments : Integer, radialSegments : Integer, p : Integer, q : Integer)
```
radius — 半径, 默认值为1.  
tube — 管道直径. 默认值为 0.4.
tubularSegments — 默认值为64.  
radialSegments — 默认值为8.  
p — 这个值决定了几何体绕旋转对称轴绕了多少圈. 默认值为2.  
q — 这个值决定了几何体绕环面的圆绕了多少圈. 默认值为3.  


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TorusKnotBufferGeometry
## 概念

创建圆环结，其特定形状由一对互质整数p和q定义。 如果p和q不是互质的，则结果将是环面链接。

## 使用
```
TorusKnotBufferGeometry(radius : Float, tube : Float, tubularSegments : Integer, radialSegments : Integer, p : Integer, q : Integer)
```
radius — 半径, 默认值为1.  
tube — 管道直径. 默认值为 0.4.
tubularSegments — 默认值为64.  
radialSegments — 默认值为8.  
p — 这个值决定了几何体绕旋转对称轴绕了多少圈. 默认值为2.  
q — 这个值决定了几何体绕环面的圆绕了多少圈. 默认值为3. 


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TubeGeometry 
## 概念
创建一个沿3d曲线挤出的管子

## 使用
```
TubeGeometry(path : Curve, tubularSegments : Integer, radius : Float, radialSegments : Integer, closed : Boolean)
```

path — Curve - 从 Curve 基本类继承而来的路径  
segments — Integer - 组成管道的分割面数量, 默认值为64  
radius — Float - 管道半径, 默认值为1  
radiusSegments — Integer - 组成截面的分割面数量, 默认值为8   
closed — Boolean 管道是开放的还是闭合的, 默认值为false   


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  


# TubeBufferGeometry 
## 概念
创建一个沿3d曲线挤出的管子

## 使用
```
TubeBufferGeometry(path : Curve, tubularSegments : Integer, radius : Float, radialSegments : Integer, closed : Boolean)
```

path — Curve - 从 Curve 基本类继承而来的路径  
segments — Integer - 组成管道的分割面数量, 默认值为64  
radius — Float - 管道半径, 默认值为1  
radiusSegments — Integer - 组成截面的分割面数量, 默认值为8   
closed — Boolean 管道是开放的还是闭合的, 默认值为false   


## 属性
### parameters : Object

具有每个构造函数参数的属性的对象。 实例化后的任何修改都不会更改几何  

# WireframeGeometry
## 概念
这可以用作辅助对象，从线框角度观察Geometry对象

## 使用
```
WireframeGeometry( geometry : Geometry )
```
geometry — 任何几何对象

