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

