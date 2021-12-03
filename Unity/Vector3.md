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

