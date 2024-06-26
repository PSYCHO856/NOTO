[toc]



### 框架大纲

### UI

#### uiOpen

```
MUIMgr.Instance.OpenUI(EMUI.MUI_WanderScene);
```

```
private System.Action action;
public override void Open(  )
{
    InitData(parms[0].ToString());
    action = (System.Action) parms[1];

    base.Open(parms);
}
```

```
MUIMgr.Instance.OpenUI(EMUI.MUISeedChoose, (Action)Grafting1Start, (Action)Grafting2Start, (Action)Grafting3Start);
```

```
MUIMgr.Instance.OpenUI(EMUI.MUIPlantChoose,(Action)(() =>
{
    CameraSJ(new Vector3(156, 30, 113), new Vector3(27, -60, 0));
    ControlEnter("Plant1Step", 0);
}));
```

直接传函数，将lambda转Action



#### messenger

```
MessageCenter.Instance.RegiseterMessage(EMsg.Switch_Component, this, MoveAction); 
```

```
MUIMgr.Instance.ShowAlert(OpenType.Long, () => { 
    Debug.Log("果树采摘完成");
    ScoreMinus();
    });
```

```
MUIMgr.Instance.ShowAlert(OpenType.TwoButton, () => { 
    Debug.Log("通用弹窗-退出窗口回调");
    ExitGame();
}, null, "退出", "是否退出当前软件？", "确定", "取消");
```



#### config csv数据

```
ResourceMgr
```



```
ConfigInfo.Instance.ReadConfig();
```

![image-20230911161206303](C:\Users\30998\AppData\Roaming\Typora\typora-user-images\image-20230911161206303.png)

#### information scriptobjects



#### mui 动画



#### UtilityTool

字典复制

延迟执行

创建物体

查找物体



#### 对象池



#### 场景控制

1开始场景载入流程

```
ResourceMgr-LoadDone
```

```
private void LoadDone(){
    if(SceneManager.GetActiveScene().buildIndex==1){
        SceneMgr.Instance.LoadSceneAsync(EScene.Level_Select.ToString());
        
        
        // EScene.Level_Select.ToString()
        Debug.Log("预加载完毕-加载选择场景");    
    }
      
}
```





2场景切换

#### 物体查找

```
stations = UtilityTool.FindChild(GameObject.Find("Environment").transform, "Stations");
```



#### UI查找

```
mainPg = UtilityTool.FindChild(GameObject.Find("Canvas").transform, "MUI_Main")
    .GetComponent<WaterElectricityMainPage>();
```





#### Bug

垃圾回收出问题

怀疑是muiloading在scenemgr后回收

```
private void LoadDone(){
    if(SceneManager.GetActiveScene().name=="Level_Load"){
        SceneMgr.Instance.LoadSceneAsync(EScene.Level_Select.ToString());
        Debug.Log("预加载完毕-加载选择场景");    
    }
    // Debug.Log("预加载完毕-加载选择场景");    
}
//resourcemgr
```

```
DontDestroyOnLoad(this);
scenemgr里加这个
```



#### ListenerUIModel

步骤+点击交互

```
ListenerPointModel
```

```
TaskMultPointMgr 事件的注册和响应
```

```
TaskMultModel任务节点
```

**怎么响应注册的事件的？**

TaskMultPointMgr 里的方法注册事件，判定名称，符合调用finish，（IListenerPoint接口里定义的listener）





```
      public void RegistFinish(Action ac){
          onFinish=null;
          onFinish=ac;//
      }
      protected void Finished(){
          threadNum++;
          if(threadNum>=registPoints.Count){
              onFinish?.Invoke();
              return;
          }
      }
      public void RegistTgV(string key,string tg,Action<string> cb=null)
{
   points[key].listener+=(v)=>{
              if(v==tg){
                  Finished();
                  points[key].listener=null;
              }
          };
          points[key].listener+=cb;
          registPoints.Add(key);
}
```

```
protected override void PlayForward(string id)
{
    base.PlayForward(id);
    listener?.Invoke("1"); //为空不执行
}
```



#### 反射

智能灌溉guidecontroller

```
var v= DeepCopyEx.DeepCopyByReflection<GuideConfig>(itor.Value);
```



数据流逻辑

深拷贝工具



#### ui遮挡功能 点击不穿透影响3d物体

```
if (EventSystem.current.IsPointerOverGameObject())
{
    return;
}
```





背包

水环境背包

黄永背包-蔬菜技能大赛背包



伯努利页面高度























伯努利框架报告报告程 

对孩子严厉=不宠他=让他将来对环境更有适应力

让他感觉你复杂，该严厉严厉该好好，但不是喜怒无常























