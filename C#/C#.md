

Null条件运算符?.和?[]

A?.B?[C];



线程安全？



=>表达式主体定义



const和readonly 静态常量和动态常量

![image-20210806104521406](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20210806104521406.png)

https://www.cnblogs.com/daidaibao/p/4214268.html



CIL c#翻译的底层语言



#### ToString

时间格式

```
public static string invertTime(int leftseconds)
{
    //Time.timeScale = 0;
    int second = leftseconds % 60;
    int hour = leftseconds / 60 / 60;
    int minute = leftseconds / 60 - hour * 60;
    return hour.ToString("00") + ":" + minute.ToString("00") + ":" + second.ToString("00");
}
```



#### using

```
using (new EditorGUI.DisabledScope(levelItemIsDragged))
{
    selectedTabIndex = GUILayout.Toolbar(selectedTabIndex, tabsNames);
}
```

自动回收（）中语句 

使用using要实现IDisposable接口

```
using (MyDispose md = new MyDispose())
{
      md.DoWork();
}

MyDispose md;
try
{
    md = new MyDispose();
    md.DoWork();
}
finally
{
    md.Dispose();
}
```



#### List

Add 将单个元素添加至表尾

AddRange 将一个集合所有元素添加至表尾





#### Dictionary

字典没有索引器是无序的,无法定义第一个

[0]不能获取第一个元素