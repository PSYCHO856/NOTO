```
#pragma warning disable 0649

using UnityEngine;

namespace Watermelon
{
    [DefaultExecutionOrder(-999)]
    [HelpURL("https://docs.google.com/document/d/1ORNWkFMZ5_Cc-BUgu9Ds1DjMjR4ozMCyr6p_GGdyCZk")]
    public class Initialiser : MonoBehaviour
    {
        [SerializeField] ProjectInitSettings initSettings;
        [SerializeField] Canvas systemCanvas;

        public static Canvas SystemCanvas;
        public static GameObject InitialiserGameObject;

        public static bool IsInititalized { get; private set; }
        public static bool IsStartInitialized { get; private set; }

        private void Awake()
        {
            Screen.sleepTimeout = SleepTimeout.NeverSleep;

            if (!IsInititalized)
            {
                IsInititalized = true;

                SystemCanvas = systemCanvas;
                InitialiserGameObject = gameObject;

                DontDestroyOnLoad(gameObject);

                initSettings.Init(this); 
            }
            else
            {
                Debug.Log("[Initialiser]: Game is already initialized!");

                Destroy(gameObject);
            }
        }

        private void Start()
        {
            if (!IsStartInitialized)
            {
                initSettings.StartInit(this);

                IsStartInitialized = true;

                AdsManager.TryToLoadFirstAds();
            }
            else
            {
                Debug.Log("[Initialiser]: Game is already initialized!");

                Destroy(gameObject);
            }
        }

        private void OnDestroy()
        {
            IsInititalized = false;
        }
    }
}

// -----------------
// Initialiser v 0.4.1
// -----------------

// Changelog
// v 0.4.1
// • Fixed error on module remove
// v 0.3.1
// • Added link to the documentation
// • Initializer renamed to Initialiser
// • Fixed problem with recompilation
// v 0.2
// • Added sorting feature
// • Initialiser MonoBehaviour will destroy after initialization
// v 0.1
// • Added basic version

```






```
private static AdsDummyHandler instance;
public static AdsDummyHandler Instance
{
    get
    {
        if (instance == null)
        {
            var singletonObject = new GameObject();
            instance = singletonObject.AddComponent<AdsDummyHandler>();
            singletonObject.name = nameof(AdsDummyHandler);
            DontDestroyOnLoad(singletonObject);
        }
        return instance;
    }
}

private AdVideoCallback adVideoCallback;
public string RewardVideoId { get; set; }

private AdsDummyController adsDummyController;


public void Init(AppConfigs appConfigs)
{
    var prefab =  (GameObject)Resources.Load("AdsDummyCanvas");
    adsDummyController = Instantiate(prefab).GetComponent<AdsDummyController>();
}

```