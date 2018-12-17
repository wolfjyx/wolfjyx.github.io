title:      "threejs 解读  material"
tags:
    - js threejs
---

# LineBasicMaterial

## 概念
用于绘制线框样式几何图形的材质  


## 使用
```
LineBasicMaterial( parameters : Object )
```
parameters -（可选）具有一个或多个属性的对象，用于定义材质的外观。 材料的任何属性（包括从Material继承的任何属性）都可以在此处传递。

属性颜色例外，它可以作为十六进制字符串传递，默认情况下为0xffffff（白色）。 Color.set（颜色）在内部调用。

## 属性

### color : Color
材质的颜色，默认设置为白色（0xffffff）

### isLineBasicMaterial : Boolean
用于检查此类或派生类是否为行基本材质。 默认为true。  
不应该更改它，因为它在内部用于优化

### lights : Boolean
材料是否受灯光影响。 默认值为false

### linewidth : Float
控制线条粗细。 默认值为1  
由于在大多数平台上WebGL渲染器的OpenGL核心配置文件的限制，无论设置值如何，线宽始终为1  

### linecap : String
定义线端的外观。 可能的值是'butt'，'round'和'square'。 默认为'round'.  
对于2D Canvas lineCap属性，WebGL渲染器会忽略该属性  

### linejoin : String
定义线关节的连接点。 可能的值是'round'，'bevel'和'miter'。 默认为'round'  
对于2D Canvas lineJoin属性，WebGL渲染器会忽略该属性   


# LineDashedMaterial
## 概念
用虚线绘制线框样式几何图形的材质

## 使用
```
LineBDashedMaterial( parameters : Object )
```
parameters -（可选）具有一个或多个属性的对象，用于定义材质的外观。 材料的任何属性（包括从Material继承的任何属性）都可以在此处传递。

属性颜色例外，它可以作为十六进制字符串传递，默认情况下为0xffffff（白色）。 Color.set（颜色）在内部调用。


## 属性
### color : Color
材质的颜色，默认设置为白色（0xffffff）

### dashSize : number  
短划线的大小, 默认值为3。

### gapSize : number
短划线间隙的大小, 默认值为1

### isLineDashedMaterial : Boolean
用于检查此类或派生类是否为行基本材质。 默认为true。  
不应该更改它，因为它在内部用于优化

### lights : Boolean
材料是否受灯光影响。 默认值为false

### linewidth : Float
控制线条粗细。 默认值为1  
由于在大多数平台上WebGL渲染器的OpenGL核心配置文件的限制，无论设置值如何，线宽始终为1  

### scale : number
线的虚线部分的比例。 默认值为1。


# Material
## 概念

材料的基础抽象类  

材质描述了对象的外观。 它们以（主要）与渲染器无关的方式定义，因此如果您决定使用不同的渲染器，则不必重写材质。

所有其他材质类型都继承了该类的属性和方法（尽管它们可能具有不同的默认值）

## 使用

```
Material()
```

创建通用材质

## 属性
### alphaTest : Float
设置运行alpha测试时要使用的alpha值。 如果不透明度低于此值，则不会渲染材质。 默认值为0  

### blendDst : Integer
混合目标。这是Three.js中定义的一个混合模式常量。默认为 OneMinusSrcAlphaFactor  
必须将材质blending设置为CustomBlending才能生效  

### blendDstAlpha : Integer
blendDst的透明度。 默认值为null

### blendEquation : Integer 
应用混合时所用的混合方程式。这是Three.js中定义的一个常量。 默认为 AddEquation  
必须将材质blending设置为CustomBlending才能生效   

### blendEquationAlpha : Integer
blendEquation的透明度。 默认值为null

### blending : Blending
当显示该材质的对象时使用何种混合模式， 必须将其设置为CustomBlending才能使用自定义blendSrc，blendDst或blendEquation，默认为 NormalBlending  

### blendSrc : Integer
混合来源。 默认为SrcAlphaFactor  
必须将材质的混合设置为CustomBlending才能生效  

### blendSrcAlpha : Integer
blendSrc的透明度。 默认值为null  

### clipIntersection : Boolean 
更改剪裁平面的方式，仅剪切其交交集，而不是它们的并集。 默认值为false  

### clippingPlanes : Array  
用户定义的剪裁平,指定为世界空间中的THREE.Plane对象。 这些平面适用于此材质所附着的对象。 空间中与平面的符号距离为负的点被剪裁（未渲染）。 这需要WebGLRenderer.localClippingEnabled为true。 默认值为null。

### clipShadows : Boolean
定义是否根据此材质上指定的剪裁平面剪切阴影。 默认值为false

### colorWrite : Boolean
是否渲染材质的颜色。 这可以与网格renderOrde属性结合使用，以创建遮挡其他对象的不可见对象，默认为true 

### customDepthMaterial : Material
渲染到深度贴图时此材质要使用的通用深度材质。 当使用DirectionalLight或SpotLight进行阴影投射时，如果您是  
（a）修改顶点着色器中的顶点位置，  
（b）使用置换贴图，  
（c）使用带alphaTest的alpha贴图  
（d）使用透明纹理 使用alphaTest  
必须为正确的阴影指定customDepthMaterial。 默认值undefined  

customDistanceMaterial : Material  
与customDepthMaterial相同，但与PointLight一起使用。 默认值undefined  

### defines : Object  

注入着色器的自定义定义。 它们以对象键/值对传递。 ```{MY_CUSTOM_DEFINE：''，PI2：Math.PI * 2}```。 这些键/值对在顶点和片段着色器中定义。 默认值undefined 

### depthFunc : Integer
使用哪种深度功能。 默认值为LessEqualDepth 

### depthTest : Boolean
是否在渲染此材质时启用深度测试。 默认为true

### depthWrite : Boolean
渲染此材质是否对深度缓冲区有任何影响。 默认为true   
在绘制2D叠加时，禁用深度写入以将多个事物分层在一起而不创建z-index伪像会很有用 

### flatShading : Boolean
定义材质是否使用平面阴影进行渲染。 默认值为false   

### fog : Boolean
材料是否受场景中fog的影响。 默认为true 

### id : Integer
此材质实例的唯一编号  

isMaterial : Boolean

用于检查此类或派生类是否为material。 默认为true,  
不应该更改它，因为它在内部用于优化  

### lights : Boolean
材质是否受光照影响，默认是true

### name : String
对象的可选名称（不必是唯一的）。 默认值为空字符串  

### needsUpdate : Boolean
指定需要重新编译材质  
实例化新材料时，此属性自动设置为true

### opacity : Float  
值得范围在0.0 - 1.0之间，表示材料的透明度。 值0.0表示完全透明，1.0表示完全不透明，  
如果材质的transparent属性未设置为true，则材质将保持完全不透明，此值仅影响其颜色   
默认值为1.0

### polygonOffset : Boolean
是否使用多边形偏移。 默认值为false。 这对应于WebGL的GL_POLYGON_OFFSET_FILL 功能。


### polygonOffsetFactor : Integer
设置多边形偏移系数。 默认值为0

### polygonOffsetUnits : Integer
设置多边形偏移单位。 默认值为0

### precision : String
覆盖此材质的渲染器的默认精度。 可以是“highp”，“mediump”或“lowp”。 默认值为null

### premultipliedAlpha : Boolean 
是否预乘alpha（透明度）值。 默认值为false 

### dithering : Boolean
是否对颜色应用抖动以消除条带的外观。 默认值为false

### shadowSide : Integer
定义面部投射阴影的哪一侧。 设置时，可以是THREE.FrontSide，THREE.BackSide或THREE.DoubleSide。 默认值为null。
如果为null，则侧面投射阴影确定如下: 

Material.side    | Side casting shadows
-------------    | -------------
THREE.FrontSide  | back side
THREE.BackSide   | front side
THREE.DoubleSide | both side

### side : Integer
定义将要渲染面部的哪一面 - 正面，背面或两者。 默认为THREE.FrontSide, 其他选项有THREE.BackSide和THREE.DoubleSide  

### transparent : Boolean
定义此材质是否透明。 这对渲染有影响，因为透明对象需要特殊处理，并在非透明对象之后呈现  
设置为true时，通过设置材质的不透明度属性来控制材质透明的程度  
默认值为false 

### type : String  
值是字符串'Material'。 这不应该更改，并且可以用于在场景中查找此类型的所有对象  


### uuid : String
此材质实例的UUID。 这会自动分配，因此不应编辑

### vertexColors : Integer
定义是否使用顶点着色。 默认值为THREE.NoColors。 其他选项有THREE.VertexColors和THREE.FaceColors。

### visible : Boolean
定义此材质是否可见。 默认为true。

### userData : object
可用于存储有关Material的自定义数据的对象。 它不应该包含对函数的引用，因为这些函数不会被克隆  

##  方法
### clone ( ) : Material 
返回与此材质具有相同参数的新材质

### copy ( material : material ) : Material
将传递材质中的参数复制到此材质中

### dispose () : null
释放材质。 材质的纹理不会被释放。 这些需要通过Texture释放  

### onBeforeCompile ( shader : Object, renderer : WebGLRenderer ) : null
在编译着色器程序之前立即执行的可选回调。 使用着色器源代码作为参数调用此函数。 用于修改内置材料 

### setValues ( values : object ) : null
values - 具有参数的容器  
根据值设置属性  

### toJSON ( meta : object ) : null
元对象，包含元素，例如材质的纹理或图像。
将材质转换为three.js JSON格式


# MeshBasicMaterial
## 概念
以简单着色（平面或线框）方式来绘制几何形状的材料  
这种材质不受光照影响  

## 使用
```
MeshBasicMaterial( parameters : Object )
```

parameters -（可选）具有一个或多个属性的对象，用于定义材质的外观。 材料的任何属性（包括从Material继承的任何属性）都可以在此处传递。

属性颜色例外，它可以作为十六进制字符串传递，默认情况下为0xffffff（白色）。 Color.set（颜色）在内部调用。

## 属性
### alphaMap : Texture
alpha贴图是一种灰度纹理，用于控制整个表面的不透明度（黑色：完全透明;白色：完全不透明）。 默认值为null。

仅使用纹理的颜色，忽略alpha通道（如果存在）。 对于RGB和RGBA纹理，WebGL渲染器在采样此纹理时将使用绿色通道，因为在DXT压缩和未压缩RGB 565格式中为绿色提供了额外的精度。 仅亮度和亮度/ alpha纹理也将按预期工作。

### aoMap : Texture
该纹理的红色通道用作环境遮挡贴图。 默认值为null。  
 aoMap需要第二组UV，因此将忽略重复和偏移纹理属性。
 
### aoMapIntensity : Float
环境遮挡效应的强度。 默认值为1.零 不遮挡效果

### color : Color
材质的颜色，默认设置为白色（0xffffff）

### combine : Integer
如何将表面颜色的结果与环境贴图（如果有）结合起来  
选项为THREE.Multiply（默认值），THREE.MixOperation，THREE.AddOperation。 如果选择混合，则使用reflectivity在两种颜色之间进行混合

### isMeshBasicMaterial : Boolean
用于检查此类或派生类是否为网格基础材质。 默认为true。
不应该更改它，因为它在内部用于优化。

### envMap : TextureCube
环境贴图。 默认值为null

### lightMap : Texture
光照贴图。 默认值为null, 
lightMap需要第二组UV，因此将忽略重复和偏移纹理属性。

### lightMapIntensity : Float
烤光的强度。 默认值为1

### lights : Boolean
材质是否受光照影响。 默认值为false

### map : Texture
颜色贴图, 默认值为null

### .morphTargets : Boolean
定义材质是否使用morphTargets。 默认值为false

### reflectivity : Float
环境贴图对表面的影响程度。 默认值为1，有效范围介于0（无反射）和1（完全反射）之间

### refractionRatio : Float
空气的折射率（IOR）（约为1）除以材料的折射率。 它与环境映射模式THREE.CubeRefractionMapping和THREE.EquirectangularRefractionMapping一起使用。 折射率不应超过1.默认值为0.98。

### skinning : Boolean
定义材质是否使用蒙皮。 默认值为false

### specularMap : Texture
材质使用的高光贴图。 默认值为null

### wireframe : Boolean
将几何图形渲染为线框。 默认值为false（即渲染为平面多边形）

### wireframeLinecap : String
定义线端的外观。 可能的值是“butt”，“round”和“square”。 默认为'round'。

这对应于2D Canvas lineCap属性，WebGL渲染器会忽略它

### wireframeLinejoin : String
定义线连接点的外观。 可能的值是“round”，“bevel”和“miter”。 默认为'round'。

这对应于2D Canvas lineJoin属性，WebGL渲染器会忽略它

### wireframeLinewidth : Float
控制线框厚度。 默认值为1。

由于在大多数平台上WebGL渲染器的OpenGL核心配置文件的限制，无论设置值如何，线宽始终为1 

# MeshDepthMaterial
## 概念
 用于按深度绘制几何图形的材质。 深度基于相机近远平面。 白色最近，黑色最远
 
## 使用
```
MeshDepthMaterial( parameters : Object )
```

parameters -（可选）具有一个或多个属性的对象，用于定义材质的外观。 材料的任何属性（包括从Material继承的任何属性）都可以在此处传递


## 属性
### alphaMap : Texture
alpha贴图是一种灰度纹理，用于控制整个表面的不透明度（黑色：完全透明;白色：完全不透明）。 默认值为null。

仅使用纹理的颜色，忽略alpha通道（如果存在）。 对于RGB和RGBA纹理，WebGL渲染器在采样此纹理时将使用绿色通道，因为在DXT压缩和未压缩RGB 565格式中为绿色提供了额外的精度。 仅亮度和亮度/ alpha纹理也将按预期工作。


### depthPacking : Constant
用于深度包装的编码, 默认为BasicDepthPacking

### displacementMap : Texture
置换贴图会影响网格顶点的位置。 与仅影响材质的光照和阴影的其他贴图不同，移位的顶点可以投射阴影，阻挡其他对象，以及充当真实的几何体。 位移纹理是这样的图像，其中每个像素的值（白色是最高的）被映射，并且重新定位网格的顶点。

### displacementScale : Float
置换贴图对网格的影响程度（黑色是不位移，白色是最大位移）。 如果没有设置置换贴图，则不会应用此值。 默认值为1。

### displacementBias : Float
位移贴图在网格顶点上的偏移量。 如果没有设置置换贴图，则不会应用此值。 默认值为0。

### fog : Boolean
材质是否受场景中fog影响。 默认值为false

### isMeshDepthMaterial : Boolean

用于检查此类或派生类是否为网格深度材质。 默认为true  
不应该更改它，因为它在内部用于优化

### lights : Boolean
材质是否受光照影响。 默认值为false

### map : Texture
颜色贴图，默认为null

### morphTargets : boolean
定义材质是否使用morphTargets。 默认值为false

### skinning : Boolean
定义材质是否使用蒙皮。 默认值为false

### wireframe : boolean
将几何图形渲染为线框。 默认值为false（即呈现为平滑着色)

### wireframeLinewidth : Float
控制线框厚度。 默认值为1。

由于在大多数平台上WebGL渲染器的OpenGL核心配置文件的限制，无论设置值如何，线宽始终为1 


# MeshLambertMaterial
## 概念
用于非光泽表面的材料，没有镜面高光  
该材料使用基于非物理的朗伯模型来计算反射率。 这可以很好地模拟一些表面（例如未经处理的木材或石材），但不能模拟具有镜面高光的光泽表面（例如涂漆木材）   
使用Gouraud着色模型计算着色。 这将计算每个顶点的着色（即在顶点着色器中）并在多边形的面上插入结果。
由于反射率和照明模型的简单性，当使用这种材料而不是MeshPhongMaterial，MeshStandardMaterial或MeshPhysicalMaterial时，性能会更高，但可能影响某些图形精度

## 使用
```
MeshLambertMaterial( parameters : Object )
```  
parameters -（可选）具有一个或多个属性的对象，用于定义材质的外观。 材料的任何属性（包括从Material继承的任何属性）都可以在此处传递。

属性颜色例外，它可以作为十六进制字符串传递，默认情况下为0xffffff（白色）。 Color.set（颜色）在内部调用 

## 属性
### alphaMap : Texture
alpha贴图是一种灰度纹理，用于控制整个表面的不透明度（黑色：完全透明;白色：完全不透明）。 默认值为null。

仅使用纹理的颜色，忽略alpha通道（如果存在）。 对于RGB和RGBA纹理，WebGL渲染器在采样此纹理时将使用绿色通道，因为在DXT压缩和未压缩RGB 565格式中为绿色提供了额外的精度。 仅亮度和亮度/ alpha纹理也将按预期工作。

### aoMap : Texture
该纹理的红色通道用作环境遮挡贴图。 默认值为null。  
 aoMap需要第二组UV，因此将忽略重复和偏移纹理属性。
 
### aoMapIntensity : Float
环境遮挡效应的强度。 默认值为1.零 不遮挡效果


### color : Color
材质的颜色，默认设置为白色（0xffffff）

### combine : Integer
如何将表面颜色的结果与环境贴图（如果有）结合起来  
选项为THREE.Multiply（默认值），THREE.MixOperation，THREE.AddOperation。 如果选择混合，则使用reflectivity在两种颜色之间进行混合

### emissive : Color
材料的发光颜色，基本上是不受其他照明影响的纯色。 默认为黑色。

### emissiveMap : Texture
设置自发光（发光）贴图。 默认值为null。 发射性地图颜色由发射颜色和发射强度调制。 如果您有自发光贴图，请务必将发光颜色设置为黑色以外的其他颜色 

### emissiveIntensity : Float
发射光的强度。 调节发光颜色。 默认值为1

### envMap : TextureCube
环境贴图。 默认值为null

### isMeshLambertMaterial : Boolean
用于检查此类或派生类是否为网格Lambert材质。 默认为true。
不应该更改它，因为它在内部用于优化

### lightMap : Texture
光照贴图。 默认值为null。 lightMap需要第二组UV，因此将忽略重复和偏移纹理属性


### lightMapIntensity : Float
烤光的强度。 默认值为1

### .map : Texture
色彩贴图，默认为null


### morphNormals : boolean
定义材质是否使用morphNormals。 设置为true可将morphNormal属性从Geometry传递到着色器。 默认值为false

### morphTargets : Boolean
定义材质是否使用morphTargets。 默认值为false

### reflectivity : Float
环境贴图对几何表面的影响程度

### refractionRatio : Float
空气的折射率（IOR）（约为1）除以材料的折射率。 它与环境映射模式THREE.CubeRefractionMapping和THREE.EquirectangularRefractionMapping一起使用。 折射率不应超过1.默认值为0.98。


### skinning : Boolean
定义材质是否使用蒙皮。 默认值为false。

### specularMap : Texture
材质使用的高光贴图。 默认值为null。


### wireframe : boolean
将几何图形渲染为线框。 默认值为false（即呈现为平滑着色)


### wireframeLinecap : String
定义线端的外观。 可能的值是“butt”，“round”和“square”。 默认为'round'。

这对应于2D Canvas lineCap属性，WebGL渲染器会忽略它

### wireframeLinejoin : String
定义线连接点的外观。 可能的值是“round”，“bevel”和“miter”。 默认为'round'。

这对应于2D Canvas lineJoin属性，WebGL渲染器会忽略它

### wireframeLinewidth : Float
控制线框厚度。 默认值为1。

由于在大多数平台上WebGL渲染器的OpenGL核心配置文件的限制，无论设置值如何，线宽始终为1 



# MeshNormalMaterial
## 概念
将法线矢量映射到RGB颜色的材质

## 使用
```
MeshNormalMaterial( parameters : Object )
```
parameters -（可选）具有一个或多个属性的对象，用于定义材质的外观。 材料的任何属性（包括从Material继承的任何属性）都可以在此处传递。

## 属性
### fog : Boolean
材质是否受场景中fog影响。 默认值为false

### isMeshNormalMaterial : Boolean
用于检查此类或派生类是否为MeshNormalMaterial材质。 默认为true  
不应该更改它，因为它在内部用于优化

### lights : Boolean
材质是否受光照影响。 默认值为false

### morphTargets : boolean
定义材质是否使用morphTargets, 默认值为false


### wireframe : boolean
将几何图形渲染为线框。 默认值为false（即呈现为平滑着色)


### wireframeLinewidth : Float
控制线框厚度。 默认值为1。

由于在大多数平台上WebGL渲染器的OpenGL核心配置文件的限制，无论设置值如何，线宽始终为1 

