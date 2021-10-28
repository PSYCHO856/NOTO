storeDatabase 定义StoreProduct[] Products 编辑器里可添加该抽象类

![image-20211019140901514](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211019140901514.png)

老奶奶 编辑器添加控制点 行走路线

编辑器undo redo reset clear

选关

```
private SerializedObject levelDatabaseSerializedObject;
```

```
private void LoadSerializedProperties()
{
    levelDatabaseSerializedObject = new SerializedObject(levelDatabase);
    levelsSerializedProperty = levelDatabaseSerializedObject.FindProperty("levels");
    obstaclesSerializedProperty = levelDatabaseSerializedObject.FindProperty("obstacles");
    movableObjectsSerializedProperty = levelDatabaseSerializedObject.FindProperty("movableObjects");
    levelsDatabaseInitialized = true;
}
```

```
private void LoadEditorTextures()
{
    placeholderTexture =
        (Texture2D) levelDatabaseSerializedObject.FindProperty("placeholderTexture").objectReferenceValue;
    greenTexture = (Texture2D) levelDatabaseSerializedObject.FindProperty("greenTexture").objectReferenceValue;
    redTexture = (Texture2D) levelDatabaseSerializedObject.FindProperty("redTexture").objectReferenceValue;
    itemBackgroundTexture = (Texture2D) levelDatabaseSerializedObject.FindProperty("itemBackgroundTexture")
        .objectReferenceValue;
}
```





模型替换





编辑器划线

鼠标点击捕获

设置界面

关卡循环！

场景栏杆

直接开始！
