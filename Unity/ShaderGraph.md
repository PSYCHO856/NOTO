

b站视频

#### 1导读

##### 几何阶段

模型空间转世界空间转摄像机空间转屏幕坐标（2d

M乘顶点坐标得世界坐标

V观察矩阵乘世界坐标得观察坐标

P最后投影变换 （受摄像机参数影响


MVP矩阵

顶点着色器vert（红旗飘飘 顶点随机变化

##### 光栅化

片元着色器frag

#### 2项目创建

edit-Projectsettings-Graphics

![image-20221114150048005](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20221114150048005.png)

lit光照模型相当于PBR

无光照

2d

贴花

![image-20221114150522065](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20221114150522065.png)

​										下面的属性是否可覆盖.jpg

Opaque不透明 Transparent



#### 溶解效果

Alpha Clipping

![image-20221114174057439](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20221114174057439.png)

小于数值就被裁切 

Step >设定值输出1 <输出0

自发光add溶解效果

Remap +time节点 



#### 水面

subtract减

clap 0-1实现平滑过渡 

颜色混合 lerp 使用t的比例将a和b混合

split 分离颜色的透明度 连给a实现透明

两张法线贴图 add type-normal

tiling and offset 连t2dUV 让法线贴图变密集

normal strength 法线凹凸度



水面起伏-定点 position节点 space选object -模型内空间

split xyz分开

combine节点 xz（不变

gradient noise 随机扰动

动态变化 用time节点修改UVoffset

水面反光和模型扭曲（波光粼粼 水下折射

smoothness 光滑度

折射

Scene Color当前屏幕已有颜色（渲染设置勾opaque texture

Screen Postion节点



自制PBR shader

todo白平衡 用于贴图+maincolor之后 可添加色温色调效果 饱和度





