[TOC]



打包图片，非2幂次贴图导致无法压缩 包体多了十几M 渲染性能下降

##### 要打图集的无所谓  单独使用的贴图长宽高必须用2的幂次

图集，所有的图片create-2d-sprite atlas

inspector中objects for packing添加图集所在文件夹，

pack preview



layout group使用





UI和画面要保证这3种分辨率下对。 iphone8，iphone x，ipad（分别代表市面上的主流分辨率）





#### 锚点

parkjam商店ui

皮肤图片preview 长分辨率位置太靠下

改变锚点位置解决 并且不会使720*1280效果变化



#### RectTransform

```
ShineTransform.sizeDelta = new Vector2(900, 900);
```



inspector面板里

​	Transform显示的是localPosition的坐标

​	RectTransform显示的是anchoredPosition3D的坐标



Width Height调用

GetComponent<RectTransform>().sizeDelta = new Vector2(width, height);





#### 适配

canvas上canvas scaler组件

ui scale mode - Scale With Screen Size



expand 灵活按宽度和高度适配



1080*720

制作ui素材也以此为准









