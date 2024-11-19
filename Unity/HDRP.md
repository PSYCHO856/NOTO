[toc]



Volume组件
        通过HDRP项目模板来创建项目，Unity会为我们自动设置好所有的HDRP高清渲染管线资源，建议保留项目窗口中的HDRPDefaultResources、Presets和Settings三个文件夹，否则需要手动生成HDRP渲染管线相关的配置文件。

​    HDRP使用Volume框架将天空的光照、阴影、后处理等设置集中到了一起。在示例场景中有一个Volume：Sky and Fog Volume负责天空、雾效效果。





 一个HDRP场景中除了包含模型外，还需要包含相机、灯光、光照探针、反射探针。然后最重要的是，使用Volume控制整个场景的光照和后处理效果。也需要使用光照贴图烘焙技术来为场景添加全局光照明。





canvas设置为screen space-overlay模式，hdrp就不会对画面进行后处理，画面不会带一层滤镜变亮

加了ui相机以后整个场景变亮、光线变冷怎么办。。

![image-20241113161647448](C:\Users\30998\AppData\Roaming\Typora\typora-user-images\image-20241113161647448.png)

https://discussions.unity.com/t/how-is-ui-supposed-to-work-in-hdrp-with-one-camera/769411/2



1. **可以为场景中一个（或者多个）相机和反射探针自定义帧设置**。 如果在这些自定义帧设置中启用某个功能（前提是在HDRP配置文件中已经启用），那么自定义帧设置中的配置信息会覆盖（Override）默认帧设置中的配置信息。

   

~~覆写hdrp的ui相机帧设置画面没有变化~~

只开抗锯齿有优化效果锯齿消失，但是画面还是会变白，覆盖global volume里的白平衡



#### UICamera配置

Inspector中Camera-Frame Settings Overrides-Rendering

Transparent Objects 勾选 后面的框取消勾选 界面上UI消失











