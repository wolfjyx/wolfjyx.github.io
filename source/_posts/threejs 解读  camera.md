title:      "threejs 解读  camera"
tags:
    - js threejs
---

# Camera
## 概念
相机的抽象类，新构建的相机都继承自此类

## 使用
创建相机：
```
Camera()
```

## 属性
### isCamera
用于检查此类或派生类是否为相机。 不应该更改此属性，因为渲染器在内部使用它进行优化。默认为true。

### layers
相机所属的layers  。 这是Object3D的继承属性。  
在渲染相机的视点时，对象必须与相机共享至少一个图层。

### matrixWorldInverse
这是matrixWorld的逆矩阵,matrixWorld包含相机在世界坐标系的变换矩阵

### projectionMatrix
包含相机的投影矩阵

### projectionMatrixInverse
projectionMatrix的逆矩阵

## 方法
### clone()
返回具有与此相同属性的新相机

### copy ( source : Camera, recursive : Boolean )
将源摄像头中的属性复制到此摄像头中

### getWorldDirection ( target : Vector3 )
target - 结果将被复制到此Vector3中   
返回表示摄像机正在查看的世界空间方向的Vector3


# CubeCamera
## 概念
创建6个渲染到**WebGLRenderTargetCube**的摄像机


## 使用
```
CubeCamera( near : Number, far : Number, cubeResolution : Number, options : Object )
```
near - 相机近剪裁距离  
far - 相机远裁剪距离   
cubeResolution - 设置立方体边缘的长度，体现为清晰度  
options - （可选）保存传递给自动生成的WebGLRenderTargetCube的纹理参数的对象。 如果未指定，则选项默认为：  
```
{format：RGBFormat，magFilter：LinearFilter，minFilter：LinearFilter}
```  
构造一个包含6个PerspectiveCameras相机渲染到WebGLRenderTargetCube

## 属性
### renderTarget
生成的立方体纹理

## 方法
### update( renderer : WebGLRenderer, scene : Scene)

调用它来更新renderTarget

### clear( renderer : WebGLRenderer, color : Boolean, depth : Boolean, stencil : Boolean )
调用此方法以清除renderTarget颜色，深度和/或模板缓冲区。 颜色缓冲区设置为渲染器的当前清晰颜色。 参数默认为true

# OrthographicCamera
## 概念
在此投影模式下，无论距离相机的距离如何，渲染图像中的对象大小都保持不变
这对于渲染2D场景和UI元素等非常有用

## 使用
```
OrthographicCamera( left : Number, right : Number, top : Number, bottom : Number, near : Number, far : Number )
```

left — 相机视锥体的左平面
right — 相机视锥体的右平面
top — 相机视锥体的上平面
bottom — 相机视锥体的下平面
near — 相机视锥体的近平面
far — 相机视锥体的原平面

这些一起定义了[相机的视锥体](https://en.wikipedia.org/wiki/Viewing_frustum)

## 属性
### bottom
相机视锥体的下平面

### far
相机视锥体的远平面。默认是2000
有效范围介于近平面和无穷远之间

### isOrthographicCamera
用于检查此类或派生类是否为正交相机。 不应该更改此属性，因为渲染器在内部使用它进行优化。默认为true。

### left
相机视锥体的左平面

### near
相机视锥体的近平面。默认是0.1
有效范围介于0和远平面

### right
相机视锥体的右平面

### top
相机视锥体的上平面

### view
通过**setViewOffset**方法设置，默认是null

### zoom
获取或设置摄像机的缩放系数, 默认值为1

## 方法
### setViewOffset ( fullWidth : Float, fullHeight : Float, x : Float, y : Float, width : Float, height : Float )

fullWidth - 多视图设置的全宽   
fullHeight - 多视图设置的全高  
x - 副摄像机的水平偏移   
y - 副摄像机的垂直偏移   
width - 副摄像机的宽度   
height - 副摄像机的高度  
 
### clearViewOffset ()
清除所有视图偏移

### updateProjectionMatrix ()
更新相机投影矩阵，必须在参数发生变化后调用

### toJSON ()
返回JSON格式的相机数据

# PerspectiveCamera
## 概念
透视相机，这种投影模式旨在模仿人眼看到的方式，它是用于渲染3D场景的最常见投影模式。

## 使用
```
PerspectiveCamera( fov : Number, aspect : Number, near : Number, far : Number )
```
fov — 相机视锥体垂直视角  
aspect — 相机视锥体宽高比  
near — 相机视锥体近平面  
far — 相机视锥体远平面  

## 属性
### aspect
相机视锥体宽高比，通常是画布宽度除以高度。默认是1

### far
相机视锥体的远截平面。默认是2000。  
有效范围介于近平面和无穷远之间。

### filmGauge
用于较大轴的胶片尺寸。 默认值为35（毫米）。 除非**filmOffset**设置为非零值，否则此参数不会影响投影矩阵。

### filmOffset
与**filmGauge**相同单位的水平偏移，默认值为0

### focus
用于立体视觉和景深效果的物距。 除非使用**StereoCamera**，否则此参数不会影响投影矩阵。 默认值为10。

### fov
相机视锥体垂直视野，从底部到顶部的视图的角度度。 默认值为50

### isPerspectiveCamera
用于检查此类或派生类是否为透视相机。 不应该更改此属性，因为渲染器在内部使用它进行优化。默认为true。

### near
相机视锥体的近截平面。默认是0.1  
有效范围大于0且小于远平面

### view
视锥体窗口规范或null。 这是使用**setViewOffset**方法设置的，并使用**clearViewOffset**清除。

### zoom
获取或设置摄像机的缩放系数, 默认值为1

## 方法
### clearViewOffset ()
删除**setViewOffset**方法设置的任何偏移量

### getEffectiveFOV()
返回乘以缩放系数 **zoom** 的当前视角，单位为角度（°）。

### getFilmHeight()
返回胶片上图像的高度,如果.aspect小于或等于1（纵向格式），则结果等于**filmGauge**

### getFilmWidth()
返回胶片上图像的宽度。 如果.aspect大于或等于1（横向格式），则结果等于**filmGauge**

### getFocalLength ()
返回当前和 **filmGauge** 有关的 **fov** 的焦距


### setFocalLength ( focalLength : Float )
设置当前和**filmGauge**有关的**fov**的焦距。
默认情况下，焦距为35mm全幅相机

### setViewOffset ( fullWidth : Float, fullHeight : Float, x : Float, y : Float, width : Float, height : Float ) 


fullWidth - 多视图设置的全宽   
fullHeight - 多视图设置的全高  
x - 副摄像机的水平偏移   
y - 副摄像机的垂直偏移   
width - 副摄像机的宽度   
height - 副摄像机的高度  

该方法用于在一个较大的视椎体中设置视图偏移。这对于多窗口或多监视器/多机设置是有用的。


.updateProjectionMatrix ()
更新相机投影矩阵，必须在参数发生变化后调用
### clone ()
返回一个 PerspectiveCamera 对象的克隆

### toJSON ()
返回JSON格式的相机数据

# StereoCamera
## 概念
立体相机。用于双透视相机，例如[3D Anaglyph](https://en.wikipedia.org/wiki/Anaglyph_3D)或者[Parallax Barrier](https://en.wikipedia.org/wiki/Parallax_barrier).

## 使用
```
StereoCamera()
```

## 属性
### aspect
相机视锥体宽高比，默认为1

### eyeSep
默认0.064

### cameraL
左相机。 这将添加到图层 - 左相机要渲染的对象也必须添加到此图层

### cameraR
右相机。 这将添加到图层 - 右相机要渲染的对象也必须添加到此图层

## 方法
### update
根据传入的相机更新立体相机

# ArrayCamera
## 概念
ArrayCamera使用预定义的一相机有效地渲染场景。 这对于渲染VR场景是重要性能考虑。
ArrayCamera的一个实例总是有一个子摄像头数组。 必须为每个子摄像机定义bounds属性，该属性确定使用此摄像机渲染的视口部分

## 使用
```
ArrayCamera( array : Array )
```
相机数组

## 属性
### cameras 
相机数组