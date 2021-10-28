```
levelDatabase = EditorUtils.GetAsset<LevelDatabase>(); watermeloncore工具类
```

```
public static Object GetAsset(Type type) UnityEditor类
{
    string[] assets = AssetDatabase.FindAssets("t:" + type.Name); 
    过滤字符filter string 
    Name: 
    l: Labels:
    t: Types:
    if (assets.Length > 0)
    {
        return AssetDatabase.LoadAssetAtPath(AssetDatabase.GUIDToAssetPath(assets[0]), type);
        //GUID 全局唯一标识符
    }

    return null;
}
```



定义：public static string[] FindAssets(string filter, ~~string[] searchInFolders~~);

