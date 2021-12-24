```
public int GetOfflineTimeToInt(TimeType type = TimeType.Minute)
{
    // DateTime nowTime = UnbiasedTime.Instance.Now();
    // long last = Convert.ToInt64(PlayerPrefs.GetString("LastTime", nowTime.ToBinary().ToString()));
    DateTime nowTime = DateTime.Now;
    long last = RecordManager.RecordData.offLineTime;
    DateTime lastTime = DateTime.FromBinary(last);//从long类型获取时间
    if (last==0)
    {
        // lastTime = UnbiasedTime.Instance.Now();
        lastTime = DateTime.Now;
    }
    TimeSpan timeSpan = nowTime.Subtract(lastTime);//计算两日期间时间差
    switch (type)
    {
        case TimeType.Hour:
            return (int) timeSpan.TotalHours;
        case TimeType.Minute:
            return (int) timeSpan.TotalMinutes;
        case TimeType.Second:
            return (int) timeSpan.TotalSeconds;
        default:
            return (int) timeSpan.TotalMinutes;
    }
}

DateTime.Now.ToBinary();
```

https://www.cnblogs.com/tmdsleep/p/5700058.html

