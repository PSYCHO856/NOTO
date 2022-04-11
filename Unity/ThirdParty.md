[TOC]

#### EnhancedScroller

http://u3d.as/fXk



#### TextMesh Pro



#### MobileKit



#### Tutorial

Resources 里tutorial文件夹里定义json文件



```json
{
  "tutorial_steps": [
{
  "target_obj": "T_CarSelect_GiftBox",
  "text": "点击按钮进入抽奖",
  "isClickable": true,
  "isReplacingNextButton": true
}
      ]
}
```


tutorialController Start里注册委托TutorialEvents.OnTutorialLoaded

tutoriaLoader里传string调用



uimanager OpenTutorial里通过单例调用load



tutorialController update里检测完成时删除委托



#### PathCreator

Bezier曲线

Vector.Lerp 线性插值 

通常用于实现 进度条0-1



```
public Vector3 GetClosestPointOnPath (Vector3 worldPoint) {
    TimeOnPathData data = CalculateClosestPointOnPathData (worldPoint);
    return Vector3.Lerp (GetPoint (data.previousIndex), GetPoint (data.nextIndex), data.percentBetweenIndices);
}

```



如何根据正上方和法线方向求得正前方

unity世界坐标系用 左手定则 叉乘就行了

Vector3

dot点乘

cross叉乘