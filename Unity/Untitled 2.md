![image-20211201185728121](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211201185728121.png)

```
#if UNITY_EDITOR
                return RuntimeEditorUtils.GetAssetByName<AudioSettings>("Audio Settings");
#else
                return audioController.settings; 
#endif
```

