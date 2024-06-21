[toc]

### EnhancedScroller



#### 03 Selection Demo背包？认知？

```
InventoryCellView
```

数据

Demo 

```
SelectionDemo Start里Reload
```

```
_data.Add(new InventoryData() { itemName = "Sword", itemCost = 123, itemDamage = 50, itemDefense = 0, itemWeight = 10, spritePath = resourcePath + "/sword", itemDescription = "Broadsword with a double-edged blade" });
```

点击事件注册

```
SelectedChanged方法里直接添加
```









### New UI Widgets

#### 言弹栏ListViewEllipse

1基本功能 第一层，填充数据即可使用

数据 

```
Scroll父物体的ListViewIcons脚本上手动添加
```

子物体 

```
ListViewIconsItemComponent脚本（DefaultItemOriginal上）
```

<font color=#FF4500 >继承了ListViewItem里面AllowItemsEvents调用ListViewCustom存储的DataSource数据                  ListViewCustom被父物体ListViewIcons继承，数据在父物体面板上添加</font>

<font color=#\#7DAC00>ListViewCustom的UpdateView调用数据使ListViewItem初始化，                                                          ListViewItem里ComponentSetData调取数据</font>

<font color=#\#7CFC >ListViewBase继承UIBehaviour继承MonoBehaviour
ListViewBase里有Start调用用virtual修饰的Init                                                          </font>

```
ListViewCustom ListViewCustomBase ListViewBase
```

被调用设置数据，添加子物体

控制器**ListViewCustom**

uiListViewIcons



2drop 通过拖拽添加和删除子内容

3点击使用

ListViewIconsItemComponent脚本面板里Events里添加















### 简单渲染效果

**场景重新烘焙 蔬菜贮藏初版**

Light面板里点烘焙





### 简单场景优化

合批 降低渲染时cpu压力

2w5

静态合批**并不减少Draw call的数量**

**在运行时，静态合批的网格会常驻内存，如果存在大量的静态合批网格，那么内存压力会十分可怕。它实际上是属于空间换时间的一种策略**





看stats batches

显卡性能



#### 根据内容自动变更scroll content长度

土工试验认知

auto

















找不到对象，不是不主动腼腆，已经变成了物质和精神匹配的问题。物质上压力，穷的。精神上因为物质不行，而看了太多东西变挑了，更找不到，看更多东西恶性循环。能找到的一般很早就找到了，太久找不到即使找到了也大概是凑合一下。
