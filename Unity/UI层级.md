[toc]





### 层级



**Camera的Depth CullingMask > Canvas的Sorting Layer > Canvas的Order in Layer**

一般**UI摄像机的Depth要大于3D摄像机的Depth，这样才能使UI在3D摄像机渲染的物体的前面显示**。

**摄像机会根据Depth从小到大的顺序，渲染各自Culling Mask的层。**

注意，在世界坐标下，物体A挡在物体B前面，但是只要渲染物体A的摄像机的Depth大于渲染物体B的摄像机的Depth，那么在Game视图中看到的效果就是物体B挡在物体A前面，如果物体A和物体B同在一个摄像机中渲染，那么正常情况下就是物体A挡住物体B（这里说正常情况下，是因为还可以通过下文的RenderQueue、SortingLayer、SortingOrder等的设置，让物体B挡在物体A前面）。

https://blog.csdn.net/woshixinyou0/article/details/127073679



Sorting Layer 在Tags&Layers设置

​	**越靠上的 SortingLayer 越先渲染**。

Order in Layer 相对于Sorting Layer的子排序，用这个值做比较时只有都在同一层时才有效。

​	**数字越小越先渲染**。

Rendering Layer Mask 



SoringLayer ：排序层级。影响物体渲染的顺序，具体的规则见后文。
Layer：层级。**用于物体的逻辑分层。**



#### 





```
int` `count = transform.parent.childCount - 1;``//Panel移
```

 

```
transform.SetSiblingIndex(count);``//Panel移位
```

https://www.cnblogs.com/domefy/p/15140208.html



#### vr项目3d物体在ui前显示的问题









### 功能

#### 让一ui在另一ui上

静态 hierachy拖到下面/变子物体

动态 Transfrom类中的函数SetSiblingIndex、SetAsFirstSibling、SetAsLastSibling

https://blog.csdn.net/qq_42139931/article/details/120433873



#### 点击不到ui

https://bbs.huaweicloud.com/blogs/294289



#### 检测鼠标在ui上

if(EventSystem.current.IsPointerOverGameObject()){Debug.Log("点击到UI");}



#### ui与3d物体层级问题

单镜头

UI一般不会被遮挡，但如果Canvas中的Render Mode 设置为Screen Space-camera或World Space，则该Canvas下的UI可以被其它物体遮挡。但该Canvas下的UI互相间仍以UI规则控制遮挡。













