WaterPuzzle Editor

Unity特性

1Editor中Inspector继承：[CustomEditor(typeof(Image), true)] true不会显示自己定义的变量

```
通过[CustomEditor(typeof(MyImage))]让myImage继承定义的MyImageEditor
```

2serializedObject为被序列化的对象，SerializedProperty为该对象上被序列化的字段。经测试，private和protected的字段要加上[SerializeField]才能被序列化，public的字段无需处理，而属性是不能被serializedObject.FindProperty(会报空)

https://www.cnblogs.com/lyh916/p/10659220.html

4 1-31

```
puzzleDatabase = EditorUtils.GetAsset<PuzzleDatabase>();
获取数据库的位置，保存在字符串中 赋值给puzzleDatabase
EditorUtils来自WatermelonCore项目
GetAsset调用Unity的AssetDatabase.LoadAssetAtPath，该方法可在运行时加载资源
----
```

```C#
FindProperty怎么继承找属性？
        private void LoadPuzzleDatabaseProperties()
        {
            puzzleDatabaseLoaded = false;
            puzzleDatabaseSO = new SerializedObject(puzzleDatabase);
            levelDataProperty = puzzleDatabaseSO.FindProperty("LevelData");
            paletteProperty = puzzleDatabaseSO.FindProperty("Palette");
            puzzleDatabaseLoaded = true;
        }
```

5 OnEnable调用LoadPuzzleDatabaseProperties初始化LevelsEditorWindow的数据

```
SerializedObject SerializedProperty Unity
```

为什么数据库要序列化 对象持久化，变为二进制数据等 

一个SerializeObject里可以添加多个属性，可同时修改共同的值

```
so.FindProperty("m_LocalPosition").vector3Value = Vector3.zero;//数据获取赋值
so.ApplyModifiedProperties();//修改
```

```
2-
InitLevelsReorderableList方法 
Undo.ClearAll(); UnityEditor

ReorderableList插件
----
为什么选用StringBuilder stringBuilder
```

~~在何时调用委托赋值~~



```C#
EditorGUILayout.BeginVertical(GUI.skin.box, GUILayout.Width(400));
EditorGUILayout.PropertyField(paletteProperty);
//序列化属性填充Box
```



```
ShowLevels-ShowLevelsList-RenameLevels
		  				 -ShowLevelSetting-ShowPreview
```



#### 问题

~~UnityEditor学习 GUI制作~~

OnGUI 76

```
private static void HandleKeyDown()
{        
     var currentEvent = Event.current;
     if (currentEvent.type == EventType.KeyDown)
     {
         if (Event.current.keyCode == KeyCode.Escape)
         {
             if (window != null)
             {
                 window.Close();
             }
             currentEvent.Use();
         }           
     }
}
```



```
ClearPaletteTextures();
```

只在使用levels时调用 清空paletteTextures字典



```
levelsReorderableList.DoLayoutList();
```

ReorderableList类 DoLayoutList GetHeight DoList方法

1关卡数据填充编辑器levels的box 2序列化数据填充瓶子Label

~~selectedLevelData.CheckValid()~~



Generate第一句调用

```
selectedLevelDataSerializedObject.ApplyModifiedProperties();
```



~~修改bottle 直接改PuzzleDatabase数据没用~~

~~只能直接改这个？~~

数据被序列化后在unity的inspector中修改



~~把water扩大~~

想改变bottleData中各属性名 次要



colorId是123456 用palette填充

colorid洗匀

编辑器数据保存



RenameLevels 未实现

问 [SearchService](https://docs.unity3d.com/2021.2/Documentation/ScriptReference/Search.SearchService.html).ShowWindow哪些是api 学习方法？

list中renamelevel方法有效？



没有拿过来的几个方法

```
private void OnDisable()
{
    ReleaseReorederableList();
    AssetDatabase.SaveAssets();
}

private void OnLostFocus()
{
    AssetDatabase.SaveAssets();
}
private void ReleaseReorederableList()
        {
            levelsReorderableList.drawHeaderCallback -= LevelsListDrawHeaderCallback;
            levelsReorderableList.drawElementCallback -= LevelsListDrawElementCallback;
            levelsReorderableList.onSelectCallback -= LevelsListOnSelectCallback;
            levelsReorderableList.onAddCallback -= LevelsListOnAddCallback;
            levelsReorderableList.onRemoveCallback -= LevelsListOnRemoveCallback;
        }
```

检验数据保存情况？

