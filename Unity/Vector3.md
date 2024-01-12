x right 红

y up绿

z forward蓝



vector3转quaternion

```
 //将transform中的rotation修改成(0,30,0)
 Vector3 rotationVector3 = new Vector3(0f, 30f, 0f);
 Quaternion rotation = Quaternion.Euler(rotationVector3);
 transform.rotation = rotation;
```



红轴为x轴、right轴，可用[Vector3](https://so.csdn.net/so/search?q=Vector3&spm=1001.2101.3001.7020).right表示

绿轴为y轴、up轴，可用Vector3.up表示

蓝轴为z轴、forward轴，可用Vector3.forward表示
