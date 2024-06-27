RCC_Settings





ui

![image-20211206111858505](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211206111858505.png)

![image-20211206111909759](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211206111909759.png)





![image-20211217141641800](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211217141641800.png)













```
using System.Collections;
using System.Collections.Generic;
using Controller;
using MobileKit;
using UnityEngine;
using UnityEngine.EventSystems;
using UnityEngine.UI;

public class GaragePaintPage : UIBasePage
{

    [SerializeField] private float waitDuration = 8;
   [SerializeField] private Button backButton;

   [SerializeField] private Button cancelButton;
   [SerializeField] private Button saveButton;
   [SerializeField] private Button settingsButton;

   [SerializeField] private UITouchDrag uiTouchDrag;


   private GarageManager garageManager;

   private float idleDuration;

   private bool startEngineSuccess;
   
   
   private void Awake()
   {
      backButton.onClick.AddListener(OnBackClick);
      

      uiTouchDrag.OnTouchDrag.AddListener(OnTouchDrag);
      uiTouchDrag.OnTouchEndDrag.AddListener(OnTouchEndDrag);
      
      settingsButton.onClick.AddListener(() =>
      {
         UIManager.Open(UIConfig.Instance.Setting);
      });
      
   }

   public override void OnOpen()
   {
      base.OnOpen();
       GarageCameraManager.Instance.ChangeTo(GarageCameraType.ObitCamera);
       GarageManager.CurrentVehicle.KillEngine();
       idleDuration = 0;
   }

   public override void OnClose()
   {
      base.OnClose();
      GarageManager.CurrentVehicle.KillEngine();
   }
   
   private void OnBackClick()
   {
      if (UIManager.IsOpened(UIConfig.Instance.Setting)) return;
      UIManager.Close(UIConfig.Instance.CarDIY);
      UIManager.Open(UIConfig.Instance.GarageOrbitPreview);
   }


   private void OnTouchDrag(PointerEventData data)
   {
      idleDuration = 0;
      GarageCameraManager.Instance.OnTouchDrag(data);
   }
   
   private void OnTouchEndDrag(PointerEventData data)
   {
      idleDuration = 0;
      GarageCameraManager.Instance.OnTouchEndDrag(data);
   }

   // private void Update()
   // {
   //     if (UIManager.IsOpened(UIConfig.Instance.Setting)) return;
   //     idleDuration += Time.deltaTime;
   //     if (idleDuration >= waitDuration)
   //     {
   //        UIManager.Close(UIConfig.Instance.CarOrbitPreview);
   //        UIManager.Open(UIConfig.Instance.CarAutoPreview);
   //     }
   // }
}
```





