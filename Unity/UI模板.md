





#### 特效

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



#### 

#### Page

```
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.EventSystems;
using UnityEngine.UI;
using DG.Tweening;
using MobileKit;
using TMPro;
using AdsManager = MobileKit.AdsManager;
using Ease = DG.Tweening.Ease;

public class SignInPage : UIBasePage
{
    [SerializeField] private Button clickPresentBtn;
    [SerializeField] private Button clickRewardBtn;
    [SerializeField] private Button clickNormalBtn;
    [SerializeField] private Button clickCloseBtn;
    private ButtonClick _clickBtnScript;
    [SerializeField] private Button closeBtn;
    [SerializeField] private SignInPageContentField[] contentFields;
    [SerializeField] private TextMeshProUGUI coinText;
    [SerializeField] private GameObject mask;
    
    private RectTransform _trans;
    private CanvasGroup _canvasGroup;
    
    private Sequence _openSequence;

    private void Awake()
    {
        _trans = GetComponent<RectTransform>();
        _canvasGroup = GetComponent<CanvasGroup>();
        _trans.localScale = Vector3.zero;
        _canvasGroup.alpha = 0;
        
        clickNormalBtn.onClick.AddListener(OnClick);
        
        clickPresentBtn.onClick.AddListener(OnClick);
        
        clickCloseBtn.onClick.AddListener(Close);

        closeBtn.onClick.AddListener(Close);
        
        _clickBtnScript = clickPresentBtn.GetComponent<ButtonClick>();
        
        _openSequence = DOTween.Sequence();
        _openSequence
            .AppendInterval(1f)
            .Append(clickNormalBtn.transform.DOScale(1f, 0.5f).SetUpdate(UpdateType.Normal, true))
            .SetRecyclable(true)
            .SetAutoKill(false)
            .Pause();
    }

    public override void OnOpen()
    {
        _canvasGroup.DOFade(1, 0.5f).SetUpdate(UpdateType.Normal, true);
        _trans.DOScale(1, 0.3f).SetUpdate(UpdateType.Normal, true);

        // coinText.text = GameController.CoinsCount.ToString();
        //UIManager.Open(ConfigManager.UIConfig.FlyCoin);
        mask.SetActive(false);

        if (AdsManager.IsRewardVideoReady())
        {
            clickRewardBtn.interactable = true;
        }
        else
        {
            clickRewardBtn.interactable = false;
        }
    }
    private void Close()
    {
        GameAudioController.PlayButtonAudio();
        _trans.DOScale(0, 0.3f).SetUpdate(UpdateType.Normal, true).OnComplete(() =>
        {
            UIManager.Close(ConfigManager.UIConfig.SignIn);
            //用于mainpage打开判断是否弹出广告 在返回challengepage打开前打开了mainpage 所以需要加判断阻止插屏弹出
            //if(GameController.enterChallengeLevel) GameController.enterChallengeLevel = false;
        });
    }
    
    private void OnClick()
    {
        mask.SetActive(true);
        
        contentFields[RecordManager.Data.GETRewardTimes % 7].DefaultStatus();
        contentFields[RecordManager.Data.GETRewardTimes % 7].RewardGetStatus();
        RecordManager.Data.GETRewardTimes++;
        RecordManager.Save();
        
    }

    private void CoinButtonsShow()
    {
        clickCloseBtn.gameObject.SetActive(false);
        clickPresentBtn.gameObject.SetActive(false);
        clickRewardBtn.gameObject.SetActive(true);
        clickNormalBtn.gameObject.SetActive(true);
        AnalyticsManager.OnRVButtonShow(ConfigManager.AdSceneConfig.RVSignMoreCoins);
    }

    private void CloseButtonShow()
    {
        clickCloseBtn.gameObject.SetActive(true);
        clickPresentBtn.gameObject.SetActive(false);
        clickRewardBtn.gameObject.SetActive(false);
        clickNormalBtn.gameObject.SetActive(false);
    }
}
```