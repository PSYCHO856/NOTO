[toc]



https://blog.csdn.net/Fenglele_Fans/article/details/82668088



```
movableObjectsSerializedProperty = levelDatabaseSerializedObject.FindProperty("movableObjects");
```

```
selectedMovableObjectSerializedObject = new SerializedObject((MovableObject)movableObjectsSerializedProperty.GetArrayElementAtIndex(index).objectReferenceValue);
```

```
selectedMovableObjectSerializedObject.FindProperty(prefabPropertyName)
```





```
//如果删除控制点 yzx 10-21
/*if (draggetElementObstacleReference.Equals((Obstacle) obstaclesSerializedProperty
    .GetArrayElementAtIndex(6).objectReferenceValue))*/
if (draggedLevelItem.FindPropertyRelative("obstacle").objectReferenceValue.Equals((Obstacle) obstaclesSerializedProperty
    .GetArrayElementAtIndex(6).objectReferenceValue))
{
    
    
    for (int i = 0; i < levelObstaclesSerializedProperty.arraySize; i++)
    {
        var nowProperty = levelObstaclesSerializedProperty.GetArrayElementAtIndex(i)
            .FindPropertyRelative("obstacle").objectReferenceValue;

        Obstacle nowObs = (Obstacle) nowProperty;
            if (nowObs.Equals((Obstacle) obstaclesSerializedProperty
                .GetArrayElementAtIndex(6).objectReferenceValue))
            {
                levelObstaclesSerializedProperty.RemoveFromVariableArrayAt(i);
                //levelObstaclesSerializedProperty.arraySize--;
                i--;
            }
    }
    //编辑器页面刷新？
    //更新Level数据里路径 
    levelWayPointsSerializedProperty.ClearArray();
}
else
{
    levelObstaclesSerializedProperty.RemoveFromVariableArrayAt(draggedLevelItemIndex);
}
```



#### 静态变量编辑器内赋值方法

```
private static TextMeshProUGUI UnlockRandomPriceText => instance.unlockRandomPriceText;
[SerializeField] TextMeshProUGUI unlockRandomPriceText;
```
