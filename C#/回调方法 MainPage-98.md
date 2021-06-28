回调方法 MainPage-98

```C#
private void OnExtraBottleClick()
{
    AudioController.PlaySound(AudioController.Sounds.Click);
    AdsManager.ShowRewardVideo(AdsDefine.RewardExtraBottle, () =>
    {
        btnExtraBottle.interactable = false;
        BottlesManager.AddEmptyBottle();
    });
}
```

lambda表达式是在执行ShowRewardVideo时发挥作用的，无参数传入被调用方法，只执行语句。

通过语句能产生一定的效果，参数a的作用如下：

```C#
        //使用Lambda表达式简化内部类的书写
        invokeCalc(10,20,(int a,int b)->{
            return a+b;
        });
```

lambda是函数，当然有需要参数的情况，只是具体参数赋值在被调用方法中实现。

最底层实现被封装 不清楚具体实现和方法功能