| 接入内容                      | 类                           | 函数                 |
| ----------------------------- | ---------------------------- | -------------------- |
| 退出游戏                      | AppManager                   | ExitGame             |
| 展示用户中心界面（设置 小人） | AppManager                   | ShowUserProtocol     |
| 五星好评（第N关结束调用）     | AppManager                   | RequestStoreReview   |
| 跳转休闲游戏专区接口          | AppManager                   | LeisureGameSubject   |
|                               |                              |                      |
| 广告接入 - **定义场景ID**     | AdsManager                   | Show****             |
|                               |                              |                      |
|                               |                              |                      |
| 安卓打点 - 关卡相关           | AnalyticsManager             | OnLevel******        |
| 安卓打点 - 激励广告点         | AnalyticsManager             | OnRVButton****       |
| 安卓打点 - 页面相关           | AnalyticsManager             | OnUMengGamePageEvent |
|                               |                              |                      |
| 安卓打点 - 广告相关           | **写到MainActivity的回调里** |                      |
|                               |                              |                      |
|                               |                              |                      |
| 展示实名信息（ios）           | RealNameAuthManager          | ShowRealNameAuthInfo |





RVSignMoreCoins 签到金币

RVSettleMoreCoins 结算金币

RVSettleSkinUnlock 结算皮肤

RVDefeatRetry 失败重试

RVShopMoreCoins 商店金币



InterSwitchIn 从后台切入

InterLevelFinish 关卡结束插屏

InterReset 重置关卡



BannerMain 正下方横幅
