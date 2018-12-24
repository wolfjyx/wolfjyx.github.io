title:      "threejs 解读  camera"
tags:
    - js threejs
---
# AmbientLight
## 概念
此光照均匀地照亮场景中的所有对象  
此灯不能用于投射阴影，因为它没有方向


## 使用
```
AmbientLight( color : Integer, intensity : Float )
```

color — 光源颜色的RGB数值, 默认0xffffff
intensity -- 光源强度的数值， 默认1

## 属性
### castShadow : Boolean
这在构造函数中设置为undefined，因为环境光不能投射阴影。

### isAmbientLight : Boolean

用于检查此类或派生类是否为环境光. 默认为true.  
不应该更改它，因为它在内部用于优化  


# DirectionalLight
## 概念
一种沿特定方向发射的光。 这种光的行为就好像它是无限远的，并且由它产生的光线都是平行的。 常见的用例是模拟日光; 太阳足够远，它的位置可以被认为是无限的，并且来自它的所有光线都是平行的。

**关于位置，目标和旋转的注释**  
方向灯的一个常见混淆点是设置旋转无效。 这是因为three.js的DirectionalLight与其他应用程序中通常称为“Target Direct Light”的东西相当。

这意味着它的方向被计算为从光的位置指向目标的位置（而不是仅具有旋转分量的'自由直接光'）。

这样做的原因是允许灯光投射阴影 - 阴影相机需要一个位置来计算阴影。


## 使用
```
DirectionalLight( color : Integer, intensity : Float )
```
color  - （可选）十六进制颜色的光。 默认值为0xffffff（白色）。
intensity - （可选）灯光强度/强度的数值。 默认值为1。

## 属性

### castShadow : Boolean
如果设置为true，则会投射动态阴影。 警告：不停的调整阴影以使其看起来正常，这很消耗性能。

### isDirectionalLight : Boolean

用于检查此类或派生类是否为平行光. 默认为true.  
不应该更改它，因为它在内部用于优化    

### position : Vector3  
这被默认设置为**Object3D.DefaultUp（0,1,0）**，以便光从上到下发光

### shadow : DirectionalLightShadow
用于计算此灯光的阴影**DirectionalLightShadow** 

### target : Object3D
DirectionalLight从其位置指向target.position。 目标的默认位置是（0,0,0）。
注意：要将目标的位置更改为默认值以外的任何位置，必须将其添加到场景中

## 方法
### copy( source : DirectionalLight ) : DirectionalLight
将source中所有属性的值复制到此DirectionalLight  


# HemisphereLight
## 概念
直接位于场景上方的光源，颜色从天空颜色渐变到底色。

此灯不能用于投射阴影

## 使用
```
HemisphereLight( skyColor : Integer, groundColor : Integer, intensity : Float )
```

skyColor - （可选）天空的十六进制颜色。 默认值为0xffffff。  
groundColor - （可选）地面的十六进制颜色。 默认值为0xffffff。  
intensity - （可选）灯光强度/强度的数值。 默认值为1。  

## 属性

### castShadow : Boolean
这在构造函数中设置为undefined，因为半球光不能投射阴影

### color : Float
灯光的天空颜色，在构造函数中传递。 默认值是（0xffffff）

### groundColor : Float
灯光的地面颜色，在构造函数中传递。 默认值是（0xffffff）


### isHemisphereLight : Boolean

用于检查此类或派生类是否为半球光. 默认为true.  
不应该更改它，因为它在内部用于优化    

### position : Vector3  
这被默认设置为**Object3D.DefaultUp（0,1,0）**，以便光从上到下发光


## 方法
### copy ( source : HemisphereLight ) : HemisphereLight
将source中 color, intensity and groundColor属性的值复制到此光照  

# Light
## 概念
灯的抽象基类 - 所有其他灯类型都继承了此处描述的属性和方法

## 使用
```
Light( color : Integer, intensity : float )
```
color - （可选）十六进制颜色的光。 默认值为0xffffff（白色）。
intensity - （可选）灯光强度/强度的数值。 默认值为1。

创造一个新的光。 请注意，这不是要直接调用（而是使用派生类之一）

## 属性
### color: Color
光的颜色。 如果未在构造函数中传递，则默认为将新颜色设置为白色

### intensity : Float
光的强度或强度。
在物理上正确的模式中，颜色*强度的乘积被解释为在坎德拉中测量的发光强度。
默认值 - 1.0

### isLight : Boolean

用于检查此类或派生类是否为光照. 默认为true.  
不应该更改它，因为它在内部用于优化  

## 方法
### copy ( source : Light ) : Light  
将source中 color, intensity 属性的值复制到此光照  

###toJSON ( meta : String )
返回JSON格式的光照数据

# PointLight
## 概念
从所有方向的单个点发出的光。 一个常见的用例是复制裸灯泡发出的光。

## 使用
```
PointLight( color : Integer, intensity : Float, distance : Number, decay : Float )
```

color - （可选）十六进制颜色的光。 默认值为0xffffff（白色）。
intensity - （可选）灯光强度/强度的数值。 默认值为1。

distance - 光的最大范围。 默认值为0（无限制）。
decay - 灯光沿着光线的距离变暗的量。 默认值为1. 对于物理上正确的照明，请将其设置为2

## 属性
### decay : Float
光线沿光线距离变暗的量  
在物理校正模式下，衰减= 2会模拟物理上逼真的光线衰减。
默认值为1。

### distance : Float
默认模式 - 当距离为零时，灯不会衰减  
 当距离不为零时，光线将从光线位置处的最大强度线性衰减到距离光线此距离处的零点  
 
 物理校正模式 - 当距离为零时，光将根据反平方定律衰减到无限远距离  
 当距离不为零时，光将根据反平方定律衰减，直到接近距离截止，然后它将快速平滑地衰减到0.当然，截止在物理上是不正确的

默认值为0.0

### isPointLight : Boolean

用于检查此类或派生类是否为点光源. 默认为true.  
不应该更改它，因为它在内部用于优化  

### power : Float 
光的强度  
在物理校正模式下，光的发光功率以流明为单位测量。 默认值为4Math.PI    
这与intensity成比例关系 ```power = intensity * 4π```  
改变这属性也将改变intensity 

###shadow : LightShadow  

用于计算此灯光阴影的LightShadow。

lightShadow的相机被设置为PerspectiveCamera，fov为90, aspect为1，near 为0.5，far为500。


## 方法
### copy  ( source : PointLight ) : PointLight
将source中所有属性的值复制到此光照  


# RectAreaLight
RectAreaLight是在一个矩形平面上均匀地发光。 这种灯型可用于模拟光源，如明亮的窗户或条形照明。

ps：

不支持阴影  
仅支持**MeshStandardMaterial**和**MeshPhysicalMaterial**  
在场景中必须包含**RectAreaLightUniformsLib**

## 使用
```
RectAreaLight( color : Integer, intensity : Float, width : Float, height : Float )
```

color - （可选）十六进制颜色的光。 默认值为0xffffff（白色）。
intensity - （可选）光的强度或亮度。 默认值为1。
width - （可选）灯的宽度。 默认值为10。
height - （可选）灯光高度。 默认值为10。

## 属性
### isRectAreaLight : Boolean

用于检查此类或派生类是否为矩形区光源. 默认为true.  
不应该更改它，因为它在内部用于优化  

## 方法
### copy  ( source : RectAreaLight ) : RectAreaLight
将source中所有属性的值复制到此光照  


# SpotLight
## 概念 
聚光源，这种光从一个方向上的单个点沿着一个锥体发出，该锥体的尺寸越大，距离得到的光越远

## 使用
```
SpotLight( color : Integer, intensity : Float, distance : Float, angle : Radians, penumbra : Float, decay : Float )
```

color - （可选）十六进制颜色的光。 默认值为0xffffff（白色）。
intensity - （可选）灯光强度/强度的数值。 默认值为1。
distance - 光的最大范围。 默认值为0（无限制）。
angle - 从其上限为Math.PI / 2的方向的最大光散射角。
pennumbra - 由于半影而衰减的聚光锥的百分比。 取值介于0和1之间。默认值为零。
decay - 灯光沿着光线的距离变暗的量

## 属性
### angle : Float
聚光灯的最大范围，从光源方向看，以弧度为单位，。 应该不超过Math.PI / 2。 默认值为Math.PI / 3

### castShadow : Boolean
如果设置为true，则会投射动态阴影。 警告：不停的调整阴影以使其看起来正常，这很消耗性能。

### decay : Float
光线沿光线距离变暗的量  
在物理校正模式下，decay= 2会导致物理上逼真的光线衰减, 
默认值为1

### distance : Float
默认模式 - 当距离为零时，灯不会衰减  
 当距离不为零时，光线将从光线位置处的最大强度线性衰减到距离光线此距离处的零点  
 
 物理校正模式 - 当距离为零时，光将根据反平方定律衰减到无限远距离  
 当距离不为零时，光将根据反平方定律衰减，直到接近距离截止，然后它将快速平滑地衰减到0.当然，截止在物理上是不正确的

默认值为0.0

### isSpotLight : Boolean

用于检查此类或派生类是否为聚光光源. 默认为true.  
不应该更改它，因为它在内部用于优化  

### penumbra : Float
由于半影而衰减的聚光锥的百分比。 取值介于0和1之间。默认值为0.0

### position : Vector3
默认设置为Object3D.DefaultUp（0,1,0），以便光从上到下发光

### power : Float
光的强度  
在物理校正模式下，光的发光功率以流明为单位测量。 默认值为4Math.PI    
这与intensity成比例关系 ```power = intensity * π```  
改变这属性也将改变intensity 

### shadow : SpotLightShadow
用于计算此灯光的阴影SpotLightShadow

### target : Object3D
Spotlight从其光源位置指向target.position。 目标的默认位置是（0,0,0）。
注意：要将目标的位置更改为默认值以外的任何位置，必须将其添加到场景中
```
scene.add( light.target ) 
```  
这样，目标的matrixWorld每帧都会自动更新

也可以将目标设置为场景中的另一个对象（具有position属性的任何对象），如下所示

	var targetObject = new THREE.Object3D();
	scene.add(targetObject);

	light.target = targetObject;
	
聚光灯现在将跟踪目标对象


## 方法
### copy  ( source : SpotLight ) : SpotLight
将source中所有属性的值复制到此光照  
