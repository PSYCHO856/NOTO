UIController 用抽象类UIBasePage实例化



场景生成

AppManager

```
platformHandler.Init();外围ui？
AdsManager.Init();
AnalyticsManager.Init();debug相关
```



DontDestoryOnLoad保护单个gobject

新场景生成方法在哪



RecordManager

?.检查不为空



#### 问题

~~调用不到控制器uicontroller~~

没设置上单例

mainpage无法赋到uicontroller上是因为其中的mainpage脚本未继承uibasepage

~~阅读recordmanager 看如何读取关卡存档~~



layoutbottles 相机与瓶子布局

事件监听 倒水 



DOTween.Sequence();

动画队列

.Append添加动画效果

在之前的动画播放结束后继续

如果想并行播放，insert

```
var s = DOTween.Sequence(); 
var Cube1RunTime = 1.0f; 
var Cube2RunTime = 1.0f; s.Append(this.m_Trans.DOLocalMoveX(2.0f, Cube1RunTime)); s.Append(this.m_Trans.DOLocalMoveX(-3.42f, Cube1RunTime)); 
//在队列动画开始后的Cube1RunTime秒后播放 s.Insert(Cube1RunTime, this.m_Other.DOLocalMoveY(2.5f, Cube2RunTime));
```



```
public void OnPointerClick(PointerEventData eventData)
{
    CheckHit(eventData.position);
```

unity获取点击事件



~~编辑器运行不能打开当前关卡~~

~~recordmanager在gamecontroller之后运行~~

调整脚本运行顺序

edit-projectsettings-script Execution Order

或者写在start里



settings文件

C#表达式主体定义=>

https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/lambda-operator



#### 未完成

~~1胜利判断条件~~

~~2isrewardvideoready 2 AdsManager.IsRewardVideoReady()~~

3本地化和textmesh pro

~~4mainpage Messenger~~

gamedefine

~~5其他controller~~

~~6gamecontroller onDisable update退出~~

7广告sdk adsmanager plugins-ads-adsyunbuhandler

8安卓打包

9rename

unity window-analysis-profiler

10svn 

1删除当下的500关 

2更新，结果+5关

revert回退到未冲突版本

11android studio

~~打包后添加瓶子按钮消失、不能看广告 moregame~~

~~mainpage制作？~~



svn://192.168.0.111/MiniGame2021/WaterPuzzle/WaterPuzzlePlus/Assets/Sprites



~~1waterlayer在瓶子下面？因为order in layer为1~~

~~2background序列化存档 需要获取指针的值赋值~~

```
selectedBackgroundProperty.objectReferenceValue = backgroundProperty.GetArrayElementAtIndex(bgn).objectReferenceValue;
```

~~4串串背景贴图是prefab？~~

~~一个瓶子四个prefab位置 读取当前位置prefab类型 对象池中实例化~~

~~8spriterenderer 掌握inspector和方法~~

9动画 有时候会有bug 没恢复原位

​	~~取消串的位移~~

​	~~串上物体移动~~ 

​		~~找当前串最上barbecue~~

​		~~记录原位置-点击上升的位置~~

​		~~domove移动~~

​		~~返回原位置，并把sprite setactive（false~~

​		setactive（false 设置位置

​		target updatelayer 

​		setactive（true

​		target domove

​		返回正常位置

#### 12无法直接修改struct waterlayer的值

13声音

14~~把倒水的画面改成串串的，包括动画啥的。~~

~~背景也要加上更换的功能，可以仿着颜色配置，在编辑器里加上~~

~~15原有存档数据删除？需要清除手机缓存~~

16广告

18dotween 延迟、手感

19看对象池

#### 20 9串屏幕缩放问题

21 在PuzzleDatabase定义背景和皮肤数据结构



1settlepage 200字体颜色

2shop字体黑白框细节

3infopage 设置 translateall bug

4settlepage 200下划线

5mainpage level



六张关卡图片制作

~~下一关时清除当前bottle卡死~~

优化 远距离倒水dotween设置长移动时间

向左和向右的判定
