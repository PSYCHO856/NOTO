# 采用泛型委托 Comparison<T>，绑定自定义的比较方法

```
_nowData.Sort((x, y) =>
{
    var xData = RecordManager.Data.GetTrainRecordDataByID(x);
    var yData = RecordManager.Data.GetTrainRecordDataByID(y);
    int qualityX = xData.qualityId;
    int qualityY = yData.qualityId;
    bool isOnTableX = xData.isOnTimeTable;
    bool isOnTableY = yData.isOnTimeTable;
    int starX = xData.stars;
    int starY = yData.stars;
    if (!isOnTableX && isOnTableY)
    {
        return 1;
    }
    if (isOnTableX == isOnTableY)
    {
        if (qualityX == qualityY)
        {
            return starY.CompareTo(starX);
        }
        return qualityY.CompareTo(qualityX);
    }
    return -1;
});
```

https://blog.csdn.net/qq_42672770/article/details/123344526