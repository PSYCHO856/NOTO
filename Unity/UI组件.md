[TOC]



#### 滚动条

#### PanelScroll

固定到某一位置

#### Button

1interactable 



2enable加黑色蒙版



两个状态切换

1做两个gobj 代码setactive

2分别设置

btn上的图片

btn上的文字

btn本身



exp1 按钮上有文字图片，点击文字图片处没有响应

解决办法：把控件移到button物体里

exp2 按钮使用非本身上的图片 Button Transition-Color Tint/Sprite Swap



```
settingsButton.onClick.AddListener(() =>
{
    UIManager.Open(UIConfig.Instance.Setting);
});
```



#### Canvas

Screen Space -OverLay

Depth值大于100 （相机最大Depth=100） 永远显示在最前面

UICamera Z值 -1000 Z>-1000并在UICamera正交投影范围内 显示在UI上



Screen Space-Camera

适用于3d场景+ui 相机投向3d场景 ui在场景和相机之间显示， 特效等需要特殊处理 重力偏差等

World Space

把UI当三维物体



Pixel Perfect-Inherit 强制画布上的元素与像素对其。仅在Screen Space模式下显示。

Override Sorting

Sort Order



#### Camera

Projection

Orthographic 正交投影

Perspective 透视投影

Rendering

Culling Mask设置为UI 只显示UI层 Canvas-Render Mode选择Screen Space -Camera



#### Slider

Slider组件中Value值拉为1

Handle Slide Area-Rect Transform left|right归零

Slider-Rect Transform调整到合适大小

Background布局变四周布局 Rect Transform

Fill Area调整锚点变四角 Rect Transform，

Fill 调整Rect Transform

 Handle Width手动调0 图片none

注意Handle



问题1形状不规则的进度条 底部圆弧 图片格式设置 剪裁

问题2结算增加动画效果

先展示之前进度

```

    private float startSliderValue;
    private float currentProgress;//页面close的时候要置0
    private float sliderDuration = 10f; //这个时间可以任意定义
    private void ProgressBar()
    {
        currentProgress += Time.deltaTime;
        rewardSlider.value = startSliderValue + currentProgress / sliderDuration;
        rewardSliderText.text = (int) (rewardSlider.value * 100) + "%";
        /*if (currentProgress >= sliderDuration)
        {
            rewardSlider.value = RecordManager.Data.RewardSliderValue*0.01f;
        }*/
    }

    private void Update()
    {
        if (rewardSlider.value < RecordManager.Data.RewardSliderValue*0.01f) ProgressBar();
    }
```



#### Image

圆形Slider实现：Image Type改Filled Radital 360 Clockwise



#### SpriteRenderer

FLIP 翻转 只影响Sprite本身 不翻转碰撞体和其他子对象



que1:

Image Type:Filled-Fill Amount 英雄联盟技能cd效果 圆形进度条等



#### Mask

比较耗费性能

一般在canvas group blocks raycasts或image的raycast target代替



#### 逻辑

点击监听

```
namespace Controller
{
    public class UITouchDrag : MonoBehaviour, IDragHandler, IEndDragHandler
    {
        public UnityEvent<PointerEventData> OnTouchDrag;
        public UnityEvent<PointerEventData> OnTouchEndDrag;
        
        public void OnDrag(PointerEventData data)
        {
            OnTouchDrag?.Invoke(data);
        }

        public void OnEndDrag(PointerEventData data)
        {
            OnTouchDrag?.Invoke(data);
        }
    }
}
```

#### Horizontal Layout Group

强制刷新布局

LayoutRebuilder.ForceRebuildLayoutImmediate(rectTransform);