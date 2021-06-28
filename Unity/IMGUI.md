IMGUI

void OnGUI () 每帧执行 类似Update

```C#
public Texture2D controlTexture;
private void OnGUI() 
{
    if (GUI.Button (new Rect (10,10,200,20), "Meet the flashing button"))
            {
                print ("You clicked me!");
            }
    GUI.Box (new Rect (0,0,100,50), "Top-left");
    GUI.Label (new Rect (0,0,100,50), "This is the text string for a Label Control");
    
    GUI.Label (new Rect (0,0,100,50), controlTexture);//贴图设置
    //第二参数可替换为new GUIContent("This is text", icon) public Texture2D icon;
}

Tooltip悬浮
----
```

Extending the Editor-Editor Windows

继承EditorWindow类，Project中创建一个文件夹命名为Editor

为Unity Editor添加菜单栏：Project中创建Editor文件夹，放入脚本

```C#
[MenuItem ("Tools/关卡编辑器 %#a")]
public static void ShowWindow() 
{
    window = GetWindow<LevelsEditorWindow>("关卡编辑器");
    window.minSize = new Vector2(800, 550);
    window.Show();
}
```



Rect 矩形参数

new Rect(x,y,width,height)

x左边界 y上边界 

注意！y坐标轴向下增大





在编辑器中使用TextField获取值 变量应该在外面定义 如果bgn在方法内定义该方法会被OnGUI调用不断刷新bgn

```
string backgroundNumber="";
EditorGUI.BeginChangeCheck();
{
    backgroundNumber = EditorGUILayout.TextField("背景编号： ", backgroundNumber);
}
if (EditorGUI.EndChangeCheck())
{
    bgn = Int32.Parse(backgroundNumber);
    Debug.Log(bgn);
}
if (GUILayout.Button("确认"))
{
    selectedBackgroundProperty =
        backgroundProperty.GetArrayElementAtIndex(bgn);
    Debug.Log(bgn);
}
```

？

```
EditorGUILayout
```

