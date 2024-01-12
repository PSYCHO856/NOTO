[toc]

### Material 材质

材料和质感 色彩 纹理 光滑度 透明度 反射率 发光度



surface type

​	opaque 不透明

​	transparent 透明

render face 渲染面数 外/内/双面渲染

metallic map 金属贴图

smoothness 平滑度

tiling 瓷砖



#### Texture 纹理 Map 贴图

被贴图包含、贴图本身是纹理 

纹理附着在具体表面叫贴图

map把texture的uv映射到3d物体表面

#### Mesh 网格

描述物体的形状

#### Shader 着色器

一段程序 将mesh和贴图颜色等按一定方式组合

可视化shader脚本

![image-20211202103212030](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211202103212030.png)

```
private static readonly int ALBEDO_ID = Shader.PropertyToID("_Albedo");
private static readonly int TINT_ID = Shader.PropertyToID("_Tint");
private static readonly int SWAPPABLE_COLOR_ID = Shader.PropertyToID("_SwappableColor");
private static readonly int GRAYSCALE_INTENSITY_ID = Shader.PropertyToID("_GrayscaleIntensity");
```

```
[SerializeField] MeshRenderer movableRenderer;
```

```
private IEnumerator ChangeTint()
{
    /*Vector4 initialTint;
    Vector4 finalTint;
    
    if (IsInteractable)
    {
        initialTint = Vector4.one * 0.6f;
        finalTint = Vector4.one;
    }
    else
    {
        initialTint = Vector4.one;
        finalTint = Vector4.one * 0.6f;
    }*/

    float duration = 1;
    float time = 0;
    do
    {
        yield return null;
        time += Time.deltaTime;

        float t = time / duration;

        //Vector4 color = initialTint + (finalTint - initialTint) * t;

        propertyBlock.SetFloat(GRAYSCALE_INTENSITY_ID, IsInteractable ? 1 - t : t);
        movableRenderer.SetPropertyBlock(propertyBlock);

    } while (time < duration);
}
```

```
movableRenderer.isVisible在相机之外 看不见 false
```



#### renderer 渲染器







#### 获取物体材质球

MeshRenderer















