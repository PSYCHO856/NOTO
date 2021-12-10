





特效

```
public override void OnOpen()
{
    Reset();
    StartCoroutine(PlayComplete());
}
```

```
public IEnumerator PlayComplete()
{
    yield return settleCompleteDelay;
    completeParticle.Play();
}
```

sorting layer同

order in layer 如果是camera渲染要比canvas大很多