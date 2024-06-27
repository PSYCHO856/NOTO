[TOC]

#### 1.0.1 广告逻辑更新

1重做 第一次免费，第二次开始右下出现图片，点击进广告

2回退 为0出图标看广告直接+5 **每次过关+1，自动回复上限为3**



为什么ratepage不跳？

if条件 只在第三关跳出、israteshow=true，虽然初始赋值false但在之前游玩recorddata里已经保存 cmd清除缓存解决



 

#### 1.0.4 8/11



区分定义nativebanner？



#### WaterPuzzleAS_Mono

##### launcher

##### rqwx

##### unityLibrary

传svn每次这两个文件要revert

build.gradle

settings.gradle



#### 广告 pc测试 AdsDummyHandler



```
public bool IsRewardVideoReady()
{
    bool ready = Random.Range(0, 2) > 0;
    Debug.Log(nameof(IsRewardVideoReady) + " " + ready);
    return false;
}
```





#### 结算金币动画数字效果

1金币动画

按钮点击处出现

2数字效果

原数字加结算奖励 过渡

3数字变动结束 关闭页面





页面动画

ispopup 最上层 

```
base.OnOpen();
```





![image-20211011164507098](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211011164507098.png)





xiaomi android树冲突





oncreate

initad



onstart里有个

ShowFullScreenVideo



permission？页面在哪





手机权限请求 在manifest里

电话权限

android.permission.READ_PHONE_STATE

https://blog.csdn.net/fenggering/article/details/53432401



1安卓代码在unity plugin下 

2找不到adsdk getdeviceid 找不到广告初始化位置

3manifest里注释掉

```
READ_PHONE_STATE
```

没用







#### sdk接入

观察给的demo工程

执行顺序

privacyActivity 里面弹申请隐私弹窗 

application 初始化vivo广告sdk

mainActivity 





application里有oncreate等等生命周期函数

```
implementation 'com.android.support:support-v4:28.0.0'
implementation 'com.android.support:recyclerview-v7:28.0.0'
implementation 'com.android.support:appcompat-v7:28.0.0'
```