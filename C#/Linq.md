# cast<T>()及OfType<T>()

//Cast<T>()用来将非泛型的序列转换为泛型的序列

DataRow row=dt.Rows.Cast<DataRow>().Single();



泛型容器：vector map list等 要指定元素类型 避免装箱拆箱等



//OfType<T>():用来将序列中可以转换的转换为指定的序列

如：一个object数组中有整数和字符串，现在想找出其中最大的数

object[] obj = {1,23,4,5,555,"aaa","bbb" };
      int max=obj.OfType<int>().Max();


字典遍历 非linq有关内容

```
foreach (var (_,platformInfo) in PlatformInfos)
{
    if (platformInfo.TrainId > 0)
    {
        SpawnTrain(platformInfo.Id, platformInfo.TrainId);
    }
}
```





```
public class Devices
{
    public void GetData()
    {
        List<string> mobiles = new List<string>() {
            "Iphone","Samsung","Nokia","MI"
        };

        //linq syntax
        var result = from s in mobiles
            where s.Contains("Nokia")
            select s;

    }
} 作者：疯狂滴小黑 https://www.bilibili.com/read/cv17582918 出处：bilibili
```





```
void FindWordInString(string text, string aimWord)
{
    text = "ttt,data";
    aimWord = "data";
    
    char[] separators = {'.', '?', '!', ' ', ';', ':', ','};
    string[] source = text.Split(separators, StringSplitOptions.RemoveEmptyEntries);
    var matchQuery = from word in source
    where word.Equals(aimWord, StringComparison.InvariantCultureIgnoreCase)
    select word;
    int wordCount = matchQuery.Count();
    Debug.Log(wordCount);
}
```



