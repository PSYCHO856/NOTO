[toc]



#### ui交互

​	控制器发出射线 

​	检测ui位置 

​	点击方法

https://blog.csdn.net/Liu_ChangC/article/details/124816737

升级版

https://blog.csdn.net/weixin_38484443/article/details/124718698?spm=1001.2014.3001.5502





ui判定——无法精确点击 为什么整个屏幕判定？

已设置的ui有效

手柄点击就触发判定 好像有什么东西锁定在button上

禁用左手 左手柄不启动会默认打出一条射线



#### 控制飞行

```
SteamVR_LaserPointer
```

```
if (interactWithUI.GetState(pose.inputSource))
{
    Debug.Log("interactWithUI.GetState ");
    Debug.Log(transform.parent.parent.position);
    

    transform.parent.parent.position += transform.forward * Speed;
}
```





Player DontDestroyOnLoad默认设置

https://steamcommunity.com/app/250820/discussions/7/1675812484344739936/

查看demo介绍场景

In case anyone comes upon this in the future, as of v2.5 (sdk 1.8.19), the Player prefab does have a check for Do Not Destroy under Player -> SteamVRObjects -> [SteamVR] -> Steam VR_Behaviour script. The info above is good practice though.





控制rts旋转

https://blog.51cto.com/u_11283245/5000337

https://blog.walterlv.com/post/unity-openvr-starting-6.html





#### 打包

有两个eventsystem影响ui点击



#### Cinemachine

https://forum.unity.com/threads/cinemachine-and-vr-switch-view-on-button-press.1106720/
