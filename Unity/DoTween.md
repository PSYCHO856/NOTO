http://dotween.demigiant.com/documentation.php



[TOC]



补间动画

大多数Tween函数以拓展方法的形式调用



## Basic Settings

```c#
using DG.Tweening;

// 使用TweenParams
TweenParams para = new TweenParams();
para.SetLoops(-1, LoopType.Yoyo);
transform.DOMove(Vector3.one, 2).SetAs(para);


transform.DOMove(position, duration)       	// 动画：目标值/偏移值 + 时长/速度
// 基本配置
    .SetSpeedBased()					// 动画基于速度而不是时长
    .From()							// 目标位置设为初始位置
    .SetRelative()					// 增量运动, true=偏移量, falese=目标值
    .SetDelay(1)						// 设置延时	  
    .SetId("Id")						// 设置动画ID

    .SetLoops(-1, LoopType.Yoyo)		// 设置循环次数和类型(重新开始，Yoyo，累加)
    .SetUpdate(UpdateType.Normal, true)  // 设置动画的帧函数, 第二个参数 TRUE = ignoreTimeScale
    
    .SetRecyclable(true)				// 设置是否可回收
    							// 为true的话，动画播放完会被回收，缓存下来，不然播完就直接销毁
    .SetAutoKill(false)				// 非无限循环的动画是否自动destroy；
    							// 若非无限循环的动画为false，停止后可以Restart(),否则不可以
    .Pause()							// 创建时处于暂停状态

// Ease曲线
	.SetEase(Ease.Linear)				// 默认Ease曲线
	.SetEase(AnimationCurve)			 // 使用AnimationCurve当作参数
	.SetEase(MyEaseFun)				// 自定义, 以回调函数为参数
              
// 回调函数
	.OnComplete(() => { })				// 动画完成回调
	.OnStepComplete( () => {})			// 完成单个循环周期时触发
	.OnKill(() => { })					// 动画销毁时回调
    
    .OnStart(() => { })					// 只在第一次播放动画时调用，在play之前调用
	.OnPlay(() => { })					// 动画播放时回调,暂停后重新播放也会调用
	.OnPause(() => { })					// 动画暂停时回调
    .OnRewind(() => { })				// 动画回退时回调, 以下情况会被调用
        									// 使用DORestart重新播放时
        									// 使用Rewind倒播动画完成时
        									// 使用DOFlip翻转动画完成时
        									// 使用DOPlayBackwards反向播放动画完成时
    .OnUpdate(() => { })				// 帧回调
    .OnWaypointChange((value) => { })	 // 在路径动画时，改变目标点时的回调，参数为当前目标点的下标
);

//返回值是运动距离的百分比 值应为0~1之间，最后的值需为1,不然停留的位置不会是目标位置
private float MyEaseFun(float time, float duration, float overshootOrAmplitude, float period)
{
    return time / duration;
}

// 
// Demo
using DG.Tweening; //引入命名空间
public class DOTWeenTest : MonoBehaviour
{
    Tweener twe; //声明一个Tweener对象
    void Start()
    { 
        twe = transform.DOMove(new Vector3(3, 4, 0), 2);//将动画保存在Tweener对象中 
                //重要 否则playbackwards不生效
        twe.Pause();//暂停,防止自动播放  
        twe.SetAutoKill(false);//关闭动画自动销毁  

    }
    //创建两个方法事件,控制前放后倒放
    public void Forward()
    {
        twe.PlayForward(); //该动画正放
    }
    public void Back()
    {
        twe.PlayBackwards(); //该动画倒放
    }
}


```



## Controlling a Tween

```c#
// 一共有三种方式控制tween动画, 所有三种方式共享相同的方法名，只是扩展方法形式增加了 DO 前缀

// 1. 通过DOTween类的静态函数控制
DOTween.PauseAll();				// All version
DOTween.Pause("badoom");		// Id version
DOTween.Pause(transform);		// target version
// 2. 直接通过tween动画控制
myTween.Pause();
// 3. 扩展方法形式
transform.DOPause();


// 如果想在动画结束之后使用这些方法，一定要disable掉 AutoKill

transform.DOPlay();				// 播放，播放的动画不能是正在播放的，也不能是播放完成的
transform.DOPause();			// 暂停此组件上的所有动画
transform.DORestart();			// 重播
transform.DORewind();			// 倒播，此方法会直接退回起始点
transform.DOSmoothRewind();		// 平滑倒播，此方法会按照之前的运动方式从当前位置退回起始点	
transform.DOKill();				// 销魂此组件上的所有动画

transform.DOFlip();				// 翻转补间的方向
transform.DOGoto(1.5f, true);	// 跳转, (跳转的时间点，跳转后是否播放动画)
transform.DOPlayBackwards();	// 反向播放动画
			// 在动画播放到一半时执行，会退回起始点，在一开始执行看不到效果是因为，物体本身就在起始点
transform.DOPlayForward();		// 正向播放动画
transfomr.TogglePause();		// 当暂停时，执行就继续播放，播放时，执行就暂停
```



## 获取动画数据

```c#
// DOTween类的静态方法
DOTween.PausedTweens();				// 返回所有暂停的动画，没有则返回null
DOTween.PlayingTweens();			// 返回所有真正播放的动画，没有则返回null
DOTween.TweensById("id", true);		// 返回对应ID的动画数组，第二个参数表示是否只收集正在播放的动画
DOTween.TweensByTarget(transform, true);	// 返回给定对象的数组
DOTween.IsTweening(transform);		// 收集传入的对象是否有动画在活动
DOTween.TotalPlayingTweens();		// 正在播放的动画的总数，目前处于延迟播放状态的动画也算

// 动画实例的方法
tweener = transform.DOMove(Vector3.one, 2);

tweener.fullPosition = 1;		// 表示动画执行位置的属性，可读可写
tweener.CompletedLoops();		// 表示动画执行完的次数
tweener.Delay();				// 获取动画的延迟时间
tweener.Duration(false);		// 获取动画的持续时间, 参数为true 表示计算循环的时间，无限循环为Infinity
tweener.Elapsed();				// 动画已播放的时间,  参数为true 表示计算循环的时间
tweener.ElapsedDirectionalPercentage(); 	// 返回动画进度的百分比, [0~1]
tweener.ElapsedPercentage(true);		// 返回动画区间已用的百分比, true=返回值是循环总区间的已用百分比
tweener.IsActive();			// 动画是否在活动
tweener.IsBackwards();				// 是否是反向动画
tweener.IsComplete();			// 动画是否完成
tweener.IsInitialized();		// 是否已经初始化
tweener.IsPlaying();			// 是否正在播放
tweener.Loops();				// 返回循环次数，无限循环为Infinity
```



## WaitFor Coroutines / Tasks

```c#
private IEnumerator PlayAnimation()
{
	tweener = transform.DOMove(Vector3.one, 2);
       
	yield return tweener.WaitForCompletion();	// 等待动画执行完

	yield return tweener.WaitForElapsedLoops(2);	// 等待指定的循环次数
        
	yield return tweener.WaitForKill();		// 等待动画被杀死
        
	yield return tweener.WaitForPosition(0.5f);	// 等待动画执行指定时间
        
    // 等待动画回退, 以下情况会继续执行函数
        // 使用DORestart重新播放时
        // 使用Rewind倒播动画完成时
        // 使用DOFlip翻转动画完成时
        // 使用DOPlayBackwards反向播放动画完成时
	yield return tweener.WaitForRewind();

	yield return tweener.WaitForStart();	// 等待Start执行后继续执行
}

private async Task PlayAnimation()
{
    myTween = transform.DOMove(Vector3.one, 2);
    await myTween.AsyncWaitForCompletion();	
    await myTween.AsyncWaitForElapsedLoops();
    await myTween.AsyncWaitForKill();
    await myTween.AsyncWaitForPosition(0.3f);
    await myTween.AsyncWaitForRewind();
    await myTween.AsyncWaitForStart();
}
```



## Tweener



### Any Value

```c#
int timer = 0;
DOTween.To( () => timer, x => timer = x, 0.2f, animDuration);
```



### Transform

```c#

transform.DOMove();			// 世界坐标移动
transform.DOLocalMove();	// 局部坐标移动

transform.DORotate(new Vector3(0, 90, 0), 2);	// 旋转到给定的值，改变的是欧拉角
transform.DORotateQuaternion(new Quaternion(0.1f, 0.1f, 0.1f, 0.1f), 2); // 旋转到给定的值，改变四元数
transform.DOLocalRotate(new Vector3(0, 90, 0), 2);
transform.DOLocalRotateQuaternion(new Quaternion(0.1f, 0.1f, 0.1f, 0.1f), 2);




//实现相机平滑运镜效果
transform.DOLookAt(new Vector3(0, 0, 0), 2);	// 平滑的让自身的z轴正方向指向目标点




transform.DOScale(new Vector3(2, 2, 2), 2);
transform.DOScaleX(3, 2);

// 冲击
transform.DOPunchPosition(new Vector3(0, 1, 0), duration, vibrato, elascity);
transform.DOPunchRotation(new Vector3(0, 90, 0), 2, 2, 0.1f);
transform.DOPunchScale(new Vector3(2, 2, 2), 2, 2, 0.1f);

// 震动
transform.DOShakePosition(1, 5, 10, 50, true);
transform.DOShakeRotation(3);
transform.DOShakeScale(3);

// 混合动画

// 原本同时执行两个Move方法，只会执行最新的一个动画命令
// 假设起始点为(0,0,0)，结果是物体运动到了（2,2,2）
transform.DOMove(new Vector3(1, 1, 1), 2);
transform.DOMove(new Vector3(2, 2, 2), 2);


// DOBlendableMoveBy允许多个同时执行, 且它是增量动画，参数不是目标点，而是要移动的量
// 假设起始点为(1,1,1)，最后动画停止时的坐标是(1,2,2)
transform.DOBlendableMoveBy(new Vector3(1, 1, 1), 1);
transform.DOBlendableMoveBy(new Vector3(-1, 0, 0), 1);  

```



### uGUI

```c#

// RectTransform
trans.DOAnchorPos()
   
// Image
image.DOFade(endValue, duration).SetAutoKill(false).Pause();	// 渐变
image.DOColor(endValue, duration).SetEase(Ease.Linear).Pause();	// 颜色
image.DOFillAmount(endValue, duration).SetEase(Ease.Linear).SetLoops(-1, LoopType.Yoyo)   //填充
    .OnStepComplete( () => {
		image.fillClockwise = !image.fillClockwise;
    }).Pause();

// Text   通过动画把现有text变成value值。（Replace, Add, Scramble）
text.DOText("This text will replace the existing one", duration).Pause();		// 替换
text.DOText("This text will be added to the existing one", duration).Pause();  	// 追加
text.DOText("This text will appear from scrambled chars", duration, true, ScrambleMode.All); // 乱码

// Slider
slider.DOValue(1, duration);			// 滑动条的值
```







### Paths

```c#
public Transform target;
public PathType pathType = PathType.CatmullRom;
public Vector3[] waypoints = new[] {
	new Vector3(4, 2, 6),
	new Vector3(8, 6, 14),
	new Vector3(4, 6, 14),
	new Vector3(0, 6, 6),
	new Vector3(-3, 0, 0)
};

void Start()
{
	// Create a path tween using the given pathType, Linear or CatmullRom (curved).
	// Use SetOptions to close the path
	// and SetLookAt to make the target orient to the path itself
	Tween t = target.DOPath(waypoints, 4, pathType)
		.SetOptions(true)
		.SetLookAt(0.001f);
	// Then set the ease to Linear and use infinite loops
	t.SetEase(Ease.Linear).SetLoops(-1);
}


// DoTween Path Component

```



### Materials

```c#
Material material;
material.DOColor(toColor, duration);						// 材质颜色
material.DOColor(Color.clear, "_Color", 2);					// 按照shader的属性名，修改颜色
material.DOColor(toColor, "_EmissionColor", duration);		// 发光
material.DOFade(0, 2);						// 修改alpha值
material.DOGradientColor(Gradient, "_Color", 3);		// 颜色渐变
material.DOOffset(new Vector2(1, 1), 2);				// 改变材质offset的值
material.DOVector(new Vector4(0, 0, 0, 1), "_Color", 3);	// 改变shader属性的名称对应的Vector4值
material.DOBlendableColor(Color.red, "_Color", 3); 		// 颜色混合
```



### Follow

```c#
public Transform target; // Target to follow
Vector3 targetLastPos;
Tweener tween;

void Start()
{
	// First create the "move to target" tween and store it as a Tweener.
	// In this case I'm also setting autoKill to FALSE so the tween can go on forever
	// (otherwise it will stop executing if it reaches the target)
	tween = transform.DOMove(target.position, 2).SetAutoKill(false);
	// Store the target's last position, so it can be used to know if it changes
	// (to prevent changing the tween if nothing actually changes)
	targetLastPos = target.position;
}

void Update()
{
	// Use an Update routine to change the tween's endValue each frame
	// so that it updates to the target's position if that changed
	if (targetLastPos == target.position) return;
	// Add a Restart in the end, so that if the tween was completed it will play again
	tween.ChangeEndValue(target.position, true).Restart();
	targetLastPos = target.position;
}

```



### Camera

```c#
camera.DOAspect(0.6f, 2);					// 屏幕视角的宽高比
camera.DOColor(Color.blue, 2);		// 改变相机background参数的颜色
camera.DONearClipPlane(200, 2);		// 改变相机近切面的值
camera.DOFarClipPlane(2000, 2);		// 改变相机远切面的值
camera.DOFieldOfView(30, 2);		// 改变相机FOV的值
camera.DOOrthoSize(endValue, duration);	// 改变相机正交大小
camera.DOPixelRect(new Rect(0f, 0f, 600f, 500f), 2);		// 按照屏幕像素计算的显示范围
camera.DORect(new Rect(0.5f, 0.5f, 0.5f, 0.5f), 2);			// 按照屏幕百分比计算的显示范围
camera.DOShakePosition(1, 10, 10, 50, false);		// 相机震动
```

## Sequence

```c#
DOTween.Sequence()		// 返回一个新的Sequence
    .Append(nestedTween)		// 添加动画到队列中
    .AppendInterval(1)		// 添加时间间隔
    .Insert(2, nestedTween)			// 按时间点插入动画, 第一个参数为时间
    .Join(nestedTween)		// 加入的动画和当前正在执行的动画一起执行
    
    .PrependCallback( () => {} )	// 前置回调， 在Sequence的最开始添加回调
    .InsertCallback(3.0f, InsertCallBack)	// 按时间点插入回调函数
    .AppendCallback(CallBack);		// 添加回调到动画中


Sequence s = DOTween.Sequence();
// 添加动画到队列中
s.Append(cube.DOMoveX(6, duration).SetRelative().SetEase(Ease.InOutQuad));
// 按时间点插入动画
s.Insert(0, cube.DORotate(new Vector3(0, 45, 0), duration / 2).SetEase(Ease.InQuad).SetLoops(2, LoopType.Yoyo));
s.Insert(duration / 2, cube.GetComponent<Renderer>().material.DOColor(Color.yellow, duration / 2));
// Set the whole Sequence to loop infinitely forward and backwards
s.SetLoops(-1, LoopType.Yoyo);
```





## Dotween Animation Component

1. 制作与设计

    ```c#
    //tips
    1. 不想直接播放，就不要选中 AutoPlay
    2. 如果非无限循环的动画如果以后想要重复播放，就不要选中 AutoKill
    
    // 例子，cube向上旋转跳跃
    Move：							Rotate：
          AutoPlay  = No 					= No
         AutoKill	= Yes					= Yes
          Duration = 2				 		2
          Delay = 0							0
        Ignore TimeScale = No				= No
          Ease OutQuard						OutQuard
          Loops -1 Yoyo						-1 Yoyo
          To = (0,4,0)						(0,180,0)
          Relative = Yes					= No
    										Rotation Mode = Fast
    
    ```
2. 代码控制
  ```c#

  // 根据ID控制动画
  // 播放
  DOTween.Restart("id");
  // 停止
  DOTween.Complete("id");

  // 控制单个 DOTweenAnimation 组件
  [SerializeField] private DOTweenAnimation bg;
  bg.DORestart();
  bg.DOPlayNext();		// 播放下一个Tween Animation
  bg.DOPlayById(id);		// 播放指定ID的动画
  bg.DOPlayAllById(id);	
  bg.DORestartById();
  bg.DORestartAllByID();
  ```

## 常见问题

1. 想要复用动画，不能调用Play()，需要调用Restart()方法

    调用play方法，这个动画 **不能是正在播放的，也不能是播放完成的，**

    Restart方法成功调用必须保证 AutoKill = false

2. 原本同时执行两个Move方法，只会执行最新的一个动画命令

     DOBlendableMoveBy允许多个同时执行, 且它是增量动画，参数不是目标点，而是要移动的量

3. 好像单纯的挂载到物体上，不激活的动画也会生效

4. playbackward要pause setautokill 先保存动画才能生效

5. 使用时会莫名其妙影响其他的动画

6. 

#### 曲线

https://easings.net/cn

https://easings.net/

线性Ease.Linear

LoopType.Restart: 当一个循环结束时，它将从头开始。
LoopType.Yoyo: 当一个循环结束时，它将向后播放，直到完成另一个循环，然后再次向前，然后再次向后，依此类推。
LoopType.Incremental: 每次循环结束时，它的 endValue 和它的 startValue 之间的差异将被添加到 endValue，从而创建随着每个循环周期增加它们的值的补间。 此循环类型仅适用于Tweeners.

```
public void DoShine(params object[] parms)
{
    // topInfoImage.DOFade(0,1f).SetLoops(8,LoopType.Yoyo).SetEase(Ease.InBack)    
    topInfoImage.DOFade(0,.45f).SetLoops(8,LoopType.Yoyo).SetEase(Ease.InQuint)    
        .OnComplete(() =>
        {
            topInfoImage.color = new Color(1, 1, 1, 1);
        });
    Text t = topInfoImage.transform.GetChild(0).GetComponent<Text>();
    t.DOFade(0,.45f).SetLoops(8,LoopType.Yoyo).SetEase(Ease.InQuint)   
        .OnComplete(() =>
        {
            t.color = new Color(1, 1, 1, 1);
        });
    
}
```

```
.OnStepComplete(()=>
{
})
```





#### 空延时操作

```
float timeCount = 0.1f;
DOTween.To(() => timeCount, a => timeCount = a, 0.1f, 1f).OnComplete(new TweenCallback(delegate
{
    //延时后的操作
}));
```



#### 提前动画配置

```
private Tweener signInAnim;
private void Awake()
{
   signInAnim = signInButton.transform.DOScale(1.1f, 1f).SetLoops(-1, LoopType.Yoyo).Pause();
}
public void UpdateSignInBtn()
{
   if (RecordManager.Data.loginDayNum > RecordManager.Data.GETRewardTimes)
   {
      signInAnim.Play();
   }
   else
   {
      signInButton.transform.localScale=Vector3.one;
      signInAnim.Pause();
   }
}
```

```
speedUpAnim = speedUpButton.transform.DOScale(0.85f, 2f).SetAutoKill(false).Pause();
```

```
speedUpAnim.Rewind();动画回退时回调
```



https://easings.net/cn



#### Dotween和Rect 

```
RectTransform rt = expFinishObj.GetComponent<RectTransform>();
finishTween = rt.DOLocalMoveX(
    rt.anchoredPosition.x-rt.sizeDelta.x, 
    2f).Pause().SetAutoKill(false);
    //好使 阵列实验
```

变换inspector上相对位置 和锚点有关



用dolocalmove 值为锚点在左上角的坐标有关



```
rectTransform.DOMove(new Vector3(x*Screen.width/width, y*Screen.height/height, z), 2);
```

```
rectTransform.DOMove(new Vector3(x, y, z), 2);
rectTransform.DOMove(new Vector3(x, Szcreen.height - y, z), 2);
rectTransform.DOMove(new Vector3(Screen.width - x,y, z), 2);
rectTransform.DOMove(new Vector3(Screen.width - x, Screen.height - y, z), 2);
```

```
showInfo = transform.GetComponent<RectTransform>().DOMoveX((-186+245*1.5f)*Screen.width/1920, 1f).SetLoops(1, LoopType.Yoyo).Pause();
```



```
unscheduledTrainList.GetComponent<RectTransform>().DOMoveY(0, duration);//终值 父物体坐标的Y值
```



```
//非一次播放动画 Restart
trafficInAnim.Restart();
```
#### Sequence不好用



#### DOAnchorPosY

```
bRect = buildPlus.GetComponent<RectTransform>();
bRectTweener = bRect.DOAnchorPosY(arrorMoveHeight, 0.5f)
    .SetEase(DG.Tweening.Ease.Linear).SetLoops(-1, LoopType.Yoyo).Pause().SetAutoKill(false);
```




有动画localScale容易出问题

建议gameobject.setactive

#### 闪烁

.SetLoops(-1,LoopType.Yoyo);