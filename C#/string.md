

修改string要赋给新字符串

```
for (int j = 0; j < tmm.taskMults.Count; j++)
{
    //去除尾部字母u
    string sname = tmm.taskMults[j].name;
    string newsname = "";
    if (sname[sname.Length - 1].Equals('u'))
    {
        sname.Remove(sname.Length - 1);
        newsname = sname.Remove(sname.Length - 1);
        Debug.Log("sname.Remove Length - 1 newsname " + newsname);
        stepObjectName.Add(newsname);

    }
    else
    {
        stepObjectName.Add(sname);

    }
    // stepObjectName.Add(tmm.taskMults[j].name);
    // Debug.Log("stepobj name" + tmm.taskMults[j].name);
}
```