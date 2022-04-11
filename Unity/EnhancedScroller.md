[TOC]





`D:\OneDrive\Assets\UI\EnhancedScroller2.31.1`

## UI Structure

```
LevelScroller 					Scroll Rect / EnhancedScroller / Mask / ScrollerController
	- Content(Scroll Rect - Content)
		- CellView					CellView
			- CellChildItem
```



## Script

### Model

```c#

```



### Cell Child Item

```c#
using System;
using System.Collections.Generic;
using System.Net.NetworkInformation;
using Feamber;
using I2.Loc;
using TMPro;
using UnityEngine;
using UnityEngine.Serialization;
using UnityEngine.UI;

public class LevelCellChildItem : MonoBehaviour
{
    [SerializeField] private Button cellBtn;
    public int Index { get; private set; }
    public Action<LevelCellChildItem> OnCellClickCallback;

    private void Awake()
    {
        cellBtn.onClick.AddListener(OnCellButtonClicked);
    }

    public void SetData(int index, Action<LevelCellChildItem> onCellClickCallback)
    {
        Index = index;
        OnCellClickCallback = onCellClickCallback;
        // todo something
    }

    public void OnCellButtonClicked()
    {
        AudioController.PlaySound(AudioController.Sounds.Click);
        OnCellClickCallback?.Invoke(this);
    }
}

```



### Cell View

```c#
using System;
using EnhancedUI.EnhancedScroller;
using UnityEngine;

public class LevelCellView : EnhancedScrollerCellView
{
    [SerializeField] private LevelCellChildItem[] levelRowCellViews;

    public void SetData(int startIndex, Action<LevelCellChildItem> selected)
    {
        for (int i = 0; i < levelRowCellViews.Length; i++)
        {
            int index = startIndex + i;
            levelRowCellViews[i].SetData(index, selected);
        }
    } 
    
}

```





### Scroller Controller

```c#
using System;
using EnhancedUI.EnhancedScroller;
using UnityEngine;
using Random = UnityEngine.Random;

public class LevelScrollerController : MonoBehaviour, IEnhancedScrollerDelegate
{
    [SerializeField] private EnhancedScroller levelScroller;
    [SerializeField] private EnhancedScrollerCellView levelCellViewPrefab;
    
    [SerializeField] private int numberOfCellsPerRow = 2;
    [SerializeField] private float cellHeight = 100;

    private int numberOfCells;
    
    private void Awake()
    {
        cellHeight = levelCellViewPrefab.GetComponent<RectTransform>().rect.height;
        levelScroller.Delegate = this;
    }
    
    // 上层Page脚本调用，设置列表数据
    public void LoadData()
    {
        int totalCount = 1000; //解锁的关卡数量
        int currentIndex = 1;
        numberOfCells = Mathf.CeilToInt((float)(totalCount + 10) / numberOfCellsPerRow);
        levelScroller.ReloadData();
        int jumpTo = currentIndex <= 21 ? 0 : numberOfCells - 2;
        levelScroller.JumpToDataIndex(jumpTo);
    }

    // 返回cell的数量
    public int GetNumberOfCells(EnhancedScroller scroller)
    {
        return numberOfCells;
    }

    // 返回cell的实际宽或高
    public float GetCellViewSize(EnhancedScroller scroller, int dataIndex)
    {
        return cellHeight;
    }

    // 传入预制体创建对象，之后可以调用函数设置数据
    public EnhancedScrollerCellView GetCellView(EnhancedScroller scroller, int dataIndex, int cellIndex)
    {
        LevelCellView levelCellView = levelScroller.GetCellView(levelCellViewPrefab) as LevelCellView;
        var index = dataIndex * numberOfCellsPerRow;
        levelCellView.name = "Cell " + index + " to " + (index + numberOfCellsPerRow - 1);
        levelCellView.SetData(index, OnCellViewSelected);
        return levelCellView;
    }

    private static void OnCellViewSelected(LevelCellChildItem cellChildItem)
    {
        if (cellChildItem != null)
        {
            RecordManager.RecordData.CurLevelIndex = cellChildItem.Index;
            GameController.Instance.StartLevel(cellChildItem.Index);
        }
    }
}

```



