## 动画状态机

[toc]



#### Animation

点击有animator组件的prefab，animation窗口才会显示

点击录制（红色按钮）界面变红， 修改prefab animation会变更



animation窗口中小竖条add event

当前动画所在prefab上挂脚本，可选择public方法



**两种创建方式** 一种点击物体 animation里create 一种project面板里创建 两种inspector里不一样 一种能用animator一种不能，只能直接animation.play



#### Animator

<font color='cornflowerblue'>Any State</font> 

所有状态的代表，如果AnyState向状态B连线，条件为A，那么同等于所有状态都向B连了一条条件为A的线



代码改变动画状态机状态

```
lotteryItems[itemIndex].boxIcon.GetComponent<Animator>().SetTrigger("BoxOpenAnim");
```

trigger执行一次后自动设置为false



初始化

```
transform.GetChild(0).GetComponent<Animator>().enabled = true;
transform.GetChild(0).GetComponent<Animator>().Play("Blend Tree");
transform.GetChild(0).GetComponent<Animator>().Update (0);
```



杆子开关

animation looptime 关

~~animator blendtree-write defaults 关~~

状态机路径无条件 has exit time关才会正常播放完

否则瞬移到动画最后一帧
