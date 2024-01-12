[toc]

#### Timeline

Window-Sequencing-Timeline

点击物体 在timeline界面create 类似animation

把物体拖入timeline界面 add animation track

​	... add from Animation CLip



时间坐标轴上add signal emitter

 inspector里add new signal receiver 选写的方法

#### Cinemachine

跟踪长镜头 不需代码

Main Camera上CinemachineBrain组件 自动查找最后添加的(setActive为true的)CinemachineVirtualCamera

##### 	CinemachineVirtualCamera

​		Follow 要跟随的物体

​			Body xyz Damping 阻尼 跟随插值

​		Look At 朝向的物体

​			Aim 默认看坐标点 调整Screen X Y/Tracked Object Offset

​			Dead Zone Width 设置死亡区域 如果目标物体走出 则相机开始移动 屏幕中间纯色部分

​			Horizontal Damping

​			Soft Zone Width 回字型蓝绿色框 人物无法走到屏幕边缘红色处

​			Bias 偏移

1Cinemachine Create Dolly Camera with Track 设置相机移动轨迹 

​	resoulution 调整轨迹平滑

​	looped 创造路径循环

2CinemachineVirtualCamera上加Animation 制作移动动画





#### 快速聚焦

ctrl shift f聚焦





























https://www.bilibili.com/video/BV1Bg411A7xz?from=search&seid=12825678121902883025&spm_id_from=333.337.0.0

