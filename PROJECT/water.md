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