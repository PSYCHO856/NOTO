```
VoiceMangan.Instance.TranInti(transform.GetComponent<AudioSource>(), transform.GetChild(0).GetChild(0).GetComponent<AudioSource>());
```



带this是进到方法类里再判断this **不是在传参前**判断

```
VoiceMangan.Instance.TranInti(this.transform.GetComponent<AudioSource>(), this.transform.GetChild(0).GetComponent<AudioSource>());
```