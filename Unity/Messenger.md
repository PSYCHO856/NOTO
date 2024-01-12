[toc]

```
MessageCenter.Instance.RegiseterMessage(EMsg.Switch_Component, this, MoveAction); //注册消息
```

```
Messenger<string>.AddListener(GameEvent.ON_CLOCK_SHOW, ShowClock);
```

有一种很常见的思想，叫委托，顾名思义就是A委托B做A想做的事情，具体实现就是A定义好函数(实现A想做的)，然后把该函数以一种特殊的形式告知B，B来调用



#### Delegate：callback 传入函数

##### 	Action：返回类型void的Delegate

##### 	Func：通过泛型自定义返回值类型，形参只能有一种





```
OnListenerAdding检验callback是否可添加
AddListener里Delegate.Combine
Remove同理
```



```
OnBroadcasting

//保存即将被调用者方法（回调方法） 广播时调用
//addlistener加的是回调方法
foreach (var callback in invocationList)
callback.Invoke();
```



messenger像第三方的中介 对回调统一管理



string Translate(string str)
{
	return str.ToUpper();
}
delegate string Delegate(string str);
void Function()
{

}
void main()
{
	// delegate
	Delegate del = Translate;del("haha");
	// Action
	Action action = Function;action("haha");
	// Func
	Func<string, string> func = Translate;
	func("haha");



Func<string, string> func = x => x.ToUpper();



#### Event：定义后简易添加监听器

**using** System;
**namespace** SimpleEvent
{
 **using** System;
 */***********发布器类***********/*
 **public** **class** EventTest
 {
  **private** **int** **value**;

  **public** **delegate** **void** NumManipulationHandler();


  **public** **event** NumManipulationHandler ChangeNum;
  **protected** **virtual** **void** OnNumChanged()
  {
   **if** ( ChangeNum != **null** )
   {
    ChangeNum(); */\* 事件被触发 \*/*
   }**else** {
    Console.WriteLine( "event not fire" );
    Console.ReadKey(); */\* 回车继续 \*/*
   }
  }


  **public** EventTest()
  {
   **int** n = 5;
   SetValue( n );
  }


  **public** **void** SetValue( **int** n )
  {
   **if** ( **value** != n )
   {
    **value** = n;
    OnNumChanged();
   }
  }
 }


 */***********订阅器类***********/*

 **public** **class** subscribEvent
 {
  **public** **void** printf()
  {
   Console.WriteLine( "event fire" );
   Console.ReadKey(); */\* 回车继续 \*/*
  }
 }

 */***********触发***********/*
 **public** **class** MainClass
 {
  **public** **static** **void** Main()
  {
   EventTest e = new EventTest(); */\* 实例化对象,第一次没有触发事件 \*/*
   subscribEvent v = new subscribEvent(); */\* 实例化对象 \*/*
   e.ChangeNum += new EventTest.NumManipulationHandler( v.printf ); */\* 注册 \*/*
   e.SetValue( 7 );
   e.SetValue( 11 );
  }
 }
}