```
public static bool SoundEnabled
{
    get
    {
        int temp=PlayerPrefs.GetInt("sound", 1);
        if (temp == 1) return true;
        return false;
    }
}
```

```
public static bool SoundEnabled=>PlayerPrefs.GetInt("sound", 1)==1;
```

这是正确的写法





#### 存档删除

搜索regedit 打开注册表

HKEY_CURRENT_USER\ Unity Software\[company name]\[product name] 

[]unity projectsetting里为准



```
persistentDataPath
```

```
StoreData.dat
```

C:\Users\Administrator\AppData\LocalLow/company Name/priduct Name



`%userprofile%\AppData\Local\Packages\[ProductPackageId]\LocalState\playerprefs.dat`.



存档格式不一致 

已经保存的存档数据中没有新增数据结构的部分 报错
