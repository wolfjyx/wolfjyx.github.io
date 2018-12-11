title:      "threejs解读 webGLRender"
tags:
    - js threejs
---

# WebGLRender
## 概念
使用WebGL渲染场景

## 使用
```
WebGLRenderer( parameters : Object )
```

* **canvas** - 绘制输出的canvas。这对应于下面的domElement属性。如果没有传值，则将创建新的canvas元素。

* **context** - 可用于将渲染器添加到现有的RenderingContext。默认值为null
* **precision** - 着色器精度。可以是“highp”，“mediump”或“lowp”。如果设备支持，则默认为“highp”
*  **alpha** 画布是否包含alpha（透明度）缓冲区。默认值为false
*  **premultipliedAlpha** 渲染器是否会假设颜色具有预乘alpha。默认为true
*  **antialias** 是否执行抗锯齿,默认值为false
*  **stencil** 绘图缓冲区是否具有至少8位的模板缓冲区。默认为true
*  **preserveDrawingBuffer** 在手动清除或覆盖之前是否保留缓冲区。默认值为false
*  **powerPreference** 向用户代理提供一个提示，指示适用于此WebGL上下文的GPU配置。可以是“high-performance”，“low-power”或“default”。默认为“default”
* **depth** 绘图缓冲区是否具有至少16位的深度缓冲区。 默认为true
* **logarithmicDepthBuffer** 是否使用对数深度缓冲区。 如果在单个场景中处理规模的巨大差异，则可能需要使用它。 默认值为false

## 属性
### autoClear: Boolean
定义渲染器是否应在渲染帧之前自动清除其输出

### autoClearColor: Boolean
如果**autoClear**为true，则定义渲染器是否应清除颜色缓冲区, 默认为true

### autoClearDepth: Boolean
如果**autoClear**为true，则定义渲染器是否应清除深度缓冲区, 默认为true

### autoClearStencil: Boolean
如果autoClear为true，则定义渲染器是否应清除模板缓冲区, 默认为true

### capabilities: Object
包含当前RenderingContext功能详细信息d的对象  
// TODO 对象属性待补充  

### clippingPlanes : Array
用户定义的在世界坐标系的裁剪平面对象。这些平面全局可用。空间中的点和该平面的点积为负将被裁剪掉。默认为 [].

### context : WebGLRenderingContext
渲染器默认通过HTMLCanvasElement.getContext（）方法其domElement获取RenderingContext上下文。  
您可以手动创建它，但它必须与domElement对应才能渲染到屏幕

### domElement：DOMElement
canvas元素。
这是由构造函数中的渲染器自动创建的（如果调用WebGLRenderer没有传入canvas）; 你只需将它添加到你的页面就像这样：
```
document.body.appendChild（renderer.domElement）;
```

### extensions : Object
**extensions.get**方法的封装，用于检查是否支持各种WebGL扩展。

### gammaFactor: Float
 默认是
 
### gammaInput：Boolean
如果设置，则所有纹理和颜色都是预乘伽马因子值。 默认值为false

### gammaOutput：Boolean
如果设置，则所有纹理和颜色需要以预乘伽马输出。 默认值为false

### info: Object
一个关于显卡内存和渲染过程统计信息的对象。便于调试和分析。该对象包含如下字段

* memory:
 * geometries
 * textures
* render:
 * calls
 * vertices
 * faces
 * points
* programs


默认情况下，这些数据会在每次渲染调用时重置，但在使用一个或多个镜像时，最好使用自定义模式重置它们：

	renderer.info.autoReset = false;
	renderer.info.reset();
	
	
### localClippingEnabled : Boolean
定义渲染器是否遵循对象级剪切平面。 默认值为false

### maxMorphTargets : Integer
着色器中允许的最大变形目标数。标准材料仅允许8个变形目标。默认值为8

### maxMorphNormals : Integer
着色器中允许的最大变形法线数。标准材料仅允许4个变形法线。默认值为4

### physicallyCorrectLights : Boolean
是否使用物理上正确的照明模式。 默认值为false

### properties : Object
由渲染器在内部使用，以跟踪各种子对象属性

### renderLists : WebGLRenderLists
在内部用于处理场景对象渲染的排序

shadowMap : WebGLShadowMap
如果使用，它包含阴影贴图的引用

### shadowMap.enabled : Boolean
如果为true,在场景中使用阴影贴图。 默认值为false

### shadowMap.autoUpdate : Boolean
启用场景中阴影的自动更新。 默认为true  
如果不需要动态光照/阴影，则可以在实例化渲染器时将其设置为false

### shadowMap.needsUpdate : Boolean
设置为true时，场景中的阴影贴图将在下一个渲染调用中更新,默认值为false
如果禁用了阴影贴图的自动更新
```shadowMap.autoUpdate = false
```
则需要将其设置为true，然后进行渲染调用以更新场景中的阴影

### shadowMap.type : Integer
定义阴影贴图类型  
选项有**THREE.BasicShadowMap**，**THREE.PCFShadowMap**（默认），**THREE.PCFSoftShadowMap**

### sortObjects : Boolean
定义渲染器是否应对对象进行排序。 默认为true  
注意：排序用于尝试正确渲染具有一定透明度的对象。 根据定义，排序对象可能无法在所有情况下使用。 根据应用的需要，可能需要关闭排序并使用其他方法来处理透明度渲染，例如， 手动确定每个对象的渲染顺序

### state : Object
包含用于设置WebGLRenderer.context状态的各种属性的函数

### toneMapping: Constant
默认为**LinearToneMapping**

### toneMappingExposur： Number
色调映射的曝光级别。 默认值为1

### toneMappingWhitePoint : Number
色调映射白点。 默认值为1

## 方法
### allocTextureUnit : Integer
尝试分配纹理单元以供着色器使用。 如果尝试分配比GPU支持更多的纹理单元，则会发出警告。 这主要用于内部

### clear ( color : Boolean, depth : Boolean, stencil : Boolean ) : null

告诉渲染器清除其颜色，深度或模板绘制缓冲区。 此方法将颜色缓冲区初始化为当前的清除色。
参数默认为true

### clearColor ( ) : null
清除颜色缓冲区。 相当于调用```clear（true，false，false）```

### clearDepth(): null
清除深度缓冲区。相当于调用```clear（false，true，false）```

### clearStencil ( ) : null
清除模板缓冲区。相当于调用```clear（false，false，true）```

### compile ( scene : Scene, camera : Camera ) : null
使用相机编译场景中的所有材质。 这对于在第一次渲染之前预编译着色器很有用

### copyFramebufferToTexture ( position : Vector2, texture : Texture, level : Number ) : null
将当前WebGLFramebuffer中的像素复制到2D纹理中

### copyTextureToTexture ( position : Vector2, srcTexture : Texture, dstTexture : Texture, level : Number ) : null
将纹理的所有像素复制到从给定位置开始的现有纹理

### dispose(): null
处理当前渲染上下文

### extensions.get ( extensionName : String ) : Object
用于检查是否支持各种扩展，并返回一个对象，其中包含扩展的详细信息（如果可用）。 此方法可以检查以下扩展名：

		- WEBGL_depth_texture
		- EXT_texture_filter_anisotropic
		- WEBGL_compressed_texture_s3tc
		- WEBGL_compressed_texture_pvrtc
		- WEBGL_compressed_texture_etc1

### forceContextLoss ( ) : null
模拟WebGL上下文的丢失。 这需要支持WEBGL_lose_context扩展

### getClearAlpha () : Float
返回具有当前clear alpha的float。 范围从0到1

### getClearColor () : Color
返回具有当前清除色的THREE.Color实例

### getContext () : WebGLRenderingContext
返回当前WebGL上下文

### getContextAttributes () : WebGLContextAttributes
返回描述在创建WebGL上下文时设置的属性的对象

### getRenderTarget () : RenderTarget
返回当前的RenderTarget（如果有）

### getCurrentViewport () : RenderTarget
返回当前视口

### getDrawingBufferSize () : Object
返回包含渲染器绘图缓冲区宽度和高度的对象，单位px

### getPixelRatio () : number
返回当前设备像素比率

### getSize () : Object
返回包含渲染器输出画布的宽度和高度的对象（单位px)

### resetGLState ( ) : null
将GL状态重置为默认值。 如果WebGL上下文丢失，则在内部调用

### readRenderTargetPixels ( renderTarget : WebGLRenderTarget, x : Float, y : Float, width : Float, height : Float, buffer ) : null

将renderTarget中的像素数据读入的缓冲区。这是WebGLRenderingContext.readPixels（）的封装函数

### render ( scene : Scene, camera : Camera, renderTarget : WebGLRenderTarget, forceClear : Boolean ) : null

使用相机渲染场景   
渲染到r**enderTarget**或canvas
如果**forceClear**为true，则即使**autoClear**属性为false，也会在渲染之前清除深度，模板和颜色缓冲区  
即使将**forceClear**设置为true，也可以通过将**autoClearColor**，**autoClearStencil**或**autoClearDepth**属性设置为false来阻止清除某些缓冲区


### renderBufferDirect ( camera : Camera, fog : Fog, geometry : Geometry, material : Material, object : Object3D, group : Object ) : null
使用相机和指定材质渲染缓冲几何集合

### renderBufferImmediate ( object : Object3D, program : shaderprogram, shading : Material ) : null
object - Object3D实例   
program - shaderProgram实例   
着色 -  Material实例   

渲染立即缓冲区。 由renderImmediateObject调用

### setAnimationLoop ( callback : Function ) : null
callback - 将在每个可用帧中调用该函数。 如果传递`null`，它将停止任何已经在进行的动画   

可以用来代替requestAnimationFrame的内置函数。 对于WebVR项目，必须使用此功能


### setClearAlpha ( alpha : Float ) : null
设置清除的alpha。 有效输入是介于0.0和1.0之间的浮点数

### setClearColor ( color : Color, alpha : Float ) : null
设置清除色和不透明度

### setPixelRatio ( value : number ) : null
设置设备像素比率。 这通常用于HiDPI设备，以防止画面模糊。

### setRenderTarget ( renderTarget : WebGLRenderTarget ) : null
renderTarget - 需要激活的renderTarget（可选）

此方法设置活动的rendertarget。 如果省略该参数，则将画布设置为活动的rendertarget

### setScissor ( x : Integer, y : Integer, width : Integer, height : Integer ) : null
将裁剪区域设置为（x，y）到（x + width，y + height）

### setScissorTest ( boolean : Boolean ) : null
启用或禁用裁剪测试。 启用此选项后，只有定义的裁剪区域内的像素才会受到其他渲染器操作的影响

### setSize ( width : Integer, height : Integer, updateStyle : Boolean ) : null

将输出画布的大小调整为（width，height），并考虑设备像素比率，将视口调整为从（0,0）开始适应该尺寸的大小。 将updateStyle设置为false可防止对输出画布进行任何样式更改

### setTexture2D ( texture : Texture, slot : number ) : null
texture - 需要设置的纹理  
slot - 指示纹理应使用哪个槽的数字  

此方法将正确的纹理设置为WebGL着色器的正确插槽。 可以找到槽号作为采样器的均匀值

### setTextureCube ( cubeTexture : CubeTexture, slot : Number ) : null

texture - 需要设置的cubeTexture。
slot - 指示纹理应使用哪个槽的数字。

此方法将正确的纹理设置为WebGL着色器的正确插槽， 可以找到槽号作为采样器的均匀值

setViewport ( x : Integer, y : Integer, width : Integer, height : Integer ) : null
将视口设置为从（x，y）到（x + width，y + height）


# WebGLRenderTarget
## 概念
显卡为后台渲染场景的缓冲区，它用于不同的效果，例如在渲染图像显示在屏幕进行后期处理

## 使用
```
WebGLRenderTarget(width : Number, height : Number, options : Object)
```
width -- renderTarget的宽度      
height -- renderTarget的高度   
options是可选的对象，保存一个自动生成的目标纹理的纹理参数以及depthBuffer / stencilBuffer布尔值  
wrapS - 默认为ClampToEdgeWrapping  
wrapT - 默认为ClampToEdgeWrapping  
magFilter - 默认为LinearFilter  
minFilter - 默认为LinearFilter  
format - 默认为RGBAFormat  
type - 默认为UnsignedByteType  
anisotropy - 默认值为1  
encoding - 默认为LinearEncoding  
depthBuffer - 默认为true。 如果您不需要，请将此设置为false  
stencilBuffer - 默认为true。 如果您不需要，请将此设置为false  


## 属性

### width : number
渲染目标的宽度

### height : number
渲染目标的高度

### scissor : Vector4
渲染目标视口内的矩形区域。 区域外的部分将被裁剪

### scissorTest : boolean
是否激活裁剪测试

### viewport : Vector4
渲染目标的视口

### texture
此纹理实例保存渲染的像素,将其用作输入以进行进一步处理

### depthBuffer : boolean
渲染到深度缓冲区。 默认为true

### stencilBuffer
渲染到深度缓冲区。 默认为true

### depthTexture : DepthTexture
如果设置，则场景深度将呈现给此纹理。 默认值为null

## 方法
### setSize ( width : Number, height : Number ) : null
设置渲染目标的尺寸

### clone () : WebGLRenderTarget
创建渲染目标的克隆

### copy ( source : WebGLRenderTarget ) : WebGLRenderTarget
采用source中渲染目标的设置到该渲染目标

### dispose () : null
调用dispose事件

# WebGLRenderTargetCube
## 概念
使用立方体相机(CubeCamera)对象来作为WebGL渲染器目标(WebGLRenderTarget)

## 使用
```
WebGLRenderTargetCube(width : Number, height : Number, options : Object)
```
width -- renderTarget的宽度    
height -- renderTarget的高度  
options是可选的对象，保存一个自动生成的目标纹理的纹理参数以及depthBuffer / stencilBuffer布尔值  
wrapS - 默认为ClampToEdgeWrapping  
wrapT - 默认为ClampToEdgeWrapping  
magFilter - 默认为LinearFilter  
minFilter - 默认为LinearFilter  
format - 默认为RGBAFormat  
type - 默认为UnsignedByteType  
anisotropy - 默认值为1  
encoding - 默认为LinearEncoding  
depthBuffer - 默认为true。 如果您不需要，请将此设置为false  
stencilBuffer - 默认为true。 如果您不需要，请将此设置为false  
## 属性
### activeCubeFace : integer
对应于立方体侧（PX 0，NX 1，PY 2，NY 3，PZ 4，NZ 5），由CubeCamera内部使用和设置
### 继承
继承自**WebGLRenderTarget**
## 方法
继承自**WebGLRenderTarget**



