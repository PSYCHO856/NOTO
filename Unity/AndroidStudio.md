



AS调Unity

反射？

Unity里 调用广告时通常用lambda实现回调函数

```
public delegate void RewardedVideoCallback();
```

```
private RewardedVideoCallback rewardedVideoCallback;
```

```
private void OnRewardVideoWatched()
{
    Debug.Log(nameof(OnRewardVideoWatched));
    rewardedVideoCallback?.Invoke();
    RewardVideoId = "";
    rewardedVideoCallback = null;
}
```

AS里  UnitySendMessage

```
RqVivo.addRewardAd(rewardId, new RqVivoAdListener.RewardAdListener() {
    @Override
    public void onVideoCached() {

    }
    @Override
    public void onRewardVerify() {
        UnityPlayer.UnitySendMessage("AdsVivoHandler", "OnRewardVideoWatched", "");
        Log.e("RqVivo测试","reward: onVideoCompletion");
    }

    @Override
    public void onAdReady() {
        hasReward = true;
    }

    @Override
    public void onAdFailed(VivoAdError vivoAdError) {
    }

    @Override
    public void onAdClick() {
        ThinkingTrackAdEvent(adEventClick, adTypeReward, adSituationReward);
    }

    @Override
    public void onAdShow() {
        ThinkingTrackAdEvent(adEventShowSuccess, adTypeReward, adSituationReward);
    }

    @Override
    public void onAdClose() {

    }

    @Override
    public void onVideoStart() {

    }

    @Override
    public void onVideoPause() {

    }

    @Override
    public void onVideoPlay() {

    }

    @Override
    public void onVideoError(VivoAdError vivoAdError) {

    }

    @Override
    public void onVideoCompletion() {

    }

    @Override
    public void onNoAd() {
        ThinkingTrackAdEvent(adEventShowFailed, adTypeReward, adSituationReward);
    }
});
```





Unity调AS

AS里

```
public static void ShowRewardVideo(String sceneId)
{
    adSituationReward = sceneId;
    mActivity.runOnUiThread(() -> {
        hasReward = false;
        RqVivo.showReward(rewardId);
        ThinkingTrackAdEvent(adEventShow, adTypeReward, adSituationReward);
    });
}
```

Unity里

```
public void ShowRewardVideo(string id, RewardedVideoCallback callback)
{
    Debug.Log(nameof(AdsVivoHandler) + " " + nameof(ShowRewardVideo) + " " + id);
    RewardVideoId = id;
    rewardedVideoCallback = callback;
    mainActivity.CallStatic("ShowRewardVideo", id);
}
```