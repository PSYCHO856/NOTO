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

