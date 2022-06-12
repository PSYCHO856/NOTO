

打包图集

项目栏create-2D-sprite atlas

菜单栏edit-projectsetting-editor-sprite packer-always enable

inspector里把图片所在文件夹拖入

图片类型要是sprite 2d

动态加载

```
public SpriteAtlas[] spriteAtlas;

public Sprite GetSpriteByName(string spriteName)
{
    if (spriteName == "") return null;
    foreach (var atlas in spriteAtlas)
    {
        var sprite = atlas.GetSprite(spriteName);
        if (sprite != null)
        {
            return sprite;
        }
    }
    Debug.LogError("Could not found sprite: " + spriteName);
    return null;
}
```

