#### unity Cannot access non-static method '' in static context

Camera.WorldToScreenPoint

实例化Camera ca.WorldToScreenPoint即可





null reference

1东西找不到 inspector里忘了赋值

2不报错也不提示

3其他的东西导致的



manifest.json红报错-unity版本 网络问题 更改版本 删除文件 重新导入

```
//shuffle mobilekit
```





重要bug

record新增

```
public List<bool> normalChallengeAdWatched = new List<bool>(15);
```



```
private void Start()
{
    
    if (RecordManager.RecordData.GetRMB.Count==0)
    {
        for (int i = 0; i < levelDatabase.cashRules.Count; i++)
        {
            RecordManager.RecordData.GetRMB.Add(false);
        }
    }
    
    if (RecordManager.RecordData.normalChallengeAdWatched.Count==0)
    {
        for (int i = 0; i < 15; i++)
        {
            RecordManager.RecordData.normalChallengeAdWatched.Add(false);
        }
    }
}
```





