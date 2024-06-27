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



#### 车出

```
StartCoroutine(MoveToFinish(LevelController.GetFinishPosition(Road)));
```









carmoderenderer

scriptobject

车辆截图





```
UnlockRandomButtonObject
```

```
closedSkinsOnCurrentPageIndexes
```

```
skinsOnCurrentPageList
```

```
productsByGroupDictionary[(StorePageName)currentPageIndex]
```

```
StoreController.Database.GetProductsByPageDictionary(CurrentProductType);
```

```？
CurrentProductType？
```

```
Enum.GetValues(typeof(StorePageName))
```

```
result.Add(page, GetProductsByPage(page, productType));
```



```
skinsOnCurrentPageList[i].BehaviourType
```

![image-20211122182114550](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211122182114550.png)





打开商店暂停游戏？



```
private static List<StoreProduct> skinsOnCurrentPageList = new List<StoreProduct>();
skinsOnCurrentPageList = productsByGroupDictionary[(StorePageName)currentPageIndex];
```



```
currentPageIndex = (int)StoreController.GetProduct(StoreController.GetSelectedProductSkinID(CurrentProductType)).Page;
```

```
private static Dictionary<StorePageName, List<StoreProduct>> productsByGroupDictionary;
productsByGroupDictionary = StoreController.Database.GetProductsByPageDictionary(CurrentProductType);*3
```





```
StoreProduct product = skinsOnCurrentPageList[itemToUnlockIndex];

if (StoreController.TryToBuyProduct(product))
{
    ChangePreview(product);
    UpdateCurrentPage(true);
}
```





```
            if (product.CanBeUnlocked())
            {
                product.Unlock();
				savedData.UnlockProduct(product.ID);
				StoreController.instance.Save();
```



```
StoreController.SelectedCharacterSkinId
```



```
StoreProduct ID
```







```
public static List<StoreProduct> skinsOnCurrentPageList = new List<StoreProduct>();
```

单例还是要public





```
foreach (StorePageName page in Enum.GetValues(typeof(StorePageName)))
{
    result.Add(page, GetProductsByPage(page, productType));
    
}
```

```
UnityEngine.Random.Range(0, lockedProductsList.Count)
```



重新生成时车有一辆车的位置变了

![image-20211206193457681](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211206193457681.png)

#### store

store database里勾is default

savedata里加数据结构

开始游戏level初始化select

添加pool

商店里选择切换





打包

playersetting里改YUNBU_ANDROID定义 ios

关debug
