[TOC]



#### TMPSettings 设置默认字体

默认字体设置在ThirdParty-TextMeshPro-Resources-TMPSettings



ui上字体不显示、内容确实 字库里没有字，再次导入检查







#### 字体效果设置

https://learn.unity.com/tutorial/textmesh-pro-working-with-material-presets#5fa30acdedbc2a01f0fb096b

hdr高光动态渲染-一张图亮部和暗部都很清晰 多张图片曝光叠图 例子：夜空+地面树木





1字体存放位置

![img](https://cdn.nlark.com/yuque/0/2021/png/21792802/1637748071098-61f44e67-582e-46d3-9993-9ea5c863f584.png)

2添加新的字体效果配置

![img](https://cdn.nlark.com/yuque/0/2021/png/21792802/1637748383661-7c1680b1-8f12-43d4-aa97-c2104c3de2b9.png)

3在场景中找到需要替换的字，选择创建的字体风格

![img](https://cdn.nlark.com/yuque/0/2021/png/21792802/1637748530570-59fb3c34-7823-43e4-8738-2e2f41c8bc47.png)





字体特效属性说明

![img](https://cdn.nlark.com/yuque/0/2021/png/21792802/1637747918977-2653dcd2-ab9c-4bf1-bde1-10cc4d08c97a.png)

![img](https://cdn.nlark.com/yuque/0/2021/png/21792802/1637747971145-7797b87a-4eb4-4332-9ad4-718c2caff61e.png)



#### project settings

![image-20211202150811605](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211202150811605.png)







```
不用inspector加i2localize
// infoText.text =
//     LocalizationManager.GetTranslation(districtController.FacilityControllers[_facilityId].TbFacilityData
//         .IDTDesc);
用加
I2.Loc.Localize localize ??= infoText.GetComponent<Localize>();
//localize.Term = "";
localize.Term = districtController.FacilityControllers[_facilityId].TbFacilityData
    .IDTDesc;
```





#### 富文本字符串模板

Loc.cs

```
public static string GetModelText<T, U>(string term, T param0, U param1)
{
    if( LocalizationManager.GetTranslation(term) == default ){
        Debug.LogWarning( $" IDT :{term} is Null "  );
        return "";
    }
    return string.Format(LocalizationManager.GetTranslation(term), param0.ToString(), param1.ToString());
}
```

```
Canvas.camera=Camera.main
```