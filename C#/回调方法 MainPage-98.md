[toc]

#### 委托

    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
    
    public class test2 : MonoBehaviour
    {
        //声明委托类型
        private delegate void MyTestDelegate(string data);
        //用委托类型声明委托事件
        private MyTestDelegate myTestEventListener;
    void Awake()
    {
        //为事件添加处理函数
        myTestEventListener += TestEventProcessFunc;
    }
    
    //为事件的处理函数
    private void TestEventProcessFunc(string data)
    {
        Debug.Log(data);
    }
    void Start()
    {
        myTestEventListener("你好世界");
    }
    }



#### 回调


    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
    
    public class test3 : MonoBehaviour
    {
        //执行函数，传一个函数作为参数，这个参数就是回调函数
        //<>里面的string，是说这个函数要是接收一个string作为参数的函数
        private void TestFunc(string data, Action<string>action)
        {
            data = "执行函数添加上前缀：" + data;
            action(data);
        }
    //这个是满足上面回调函数格式的函数
    private void myAction(string data)
    {
        Debug.Log(data);
    }
    // Start is called before the first frame update
    void Start()
    {
        TestFunc("你好世界", myAction);
    }
    }
区别：
从代码上可以看出，一个委托声明的事件用的是+=，也就是说，可以添加很多个委托声明，一旦进行出发，那么将会按照订阅的顺序，也就是+=的顺序进行全部的调用
从思路上来说，回调就相当于把特定格式的函数当作参数传递，而回调更类似于订阅，用特定格式的委托声明了一个事件，很多符合委托格式的函数都可以进行+=订阅
委托是根据委托类型来声明事件，而委托类型决定了声明的事件可以由哪些函数来进行订阅，这种思路好像是要比函数会掉路走得更宽，更有层次感。

原文链接：https://blog.csdn.net/qq_40666620/article/details/107896358



我们使用打电话的场景来描述回调的机制，**普通的函数调用**类似于给一个人打电话，向对方提了一个问题，获取对方的答案，然后挂掉电话；而**回调机制**就是：你给这个人打电话，向他提了一个问题，留下你的姓名和电话号，然后挂掉电话，等待他在合适的时候给你答复。

我的理解：调用a执行的时候，实际上让b执行了，b可以进行一些操作刷新状态，也让a得到了条件继续执行完毕



我要去火星了.

好,那你回来之后要娶我,我要给你生猴子.



十年过去后,他从火星回来了,娶了她.

#### 回调方法 MainPage-98

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

#### 回调方法 NormalChallengeContentField

```
	2public void UpdateItem(int index,Action<int> onContentClick)
	{
		...
        btnChallenge.onClick.AddListener(() => onContentClick(index));
    }Content里
```

```
	1private void UpdateItems()
    {
        for (int i = 0; i < normalContentFields.Length; i++)
        {
            normalContentFields[i].UpdateItem(i, OnContentButtonClick);
        }
    }
    3private void OnContentButtonClick(int index)
    {
        //挑战
        AudioManager.PlaySound(ConfigManager.AudioConfig.Click);
        
        GameController.CurNormalChallengeLevelIndex = index;

        //AnalyticsManager.OnLevelUseItem(GameController.CurLevelIndex + 1, 3);
        UIManager.Close(ConfigManager.UIConfig.NormalChallenge);
        UIManager.Open(ConfigManager.UIConfig.FirstNormalChallenge);
    }Page里
```

解耦了

#### 广播 Messenger

只需要知道自己把信息发出去了

一个标志位只能对应一种类型

