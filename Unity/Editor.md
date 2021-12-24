editorwindow.repaint update中调用 窗口重绘





currentEvent.button()

​						.Use()





```
[CustomEditor(typeof(AudioSettings))]
public class AudioSettingsEditor : WatermelonEditor
{
    private const string audioEnabledPropertyName = "isAudioEnabled";
    private const string musicEnabledPropertyName = "isMusicEnabled";
    private const string vibrationEnabledPropertyName = "isVibrationEnabled";

    private const string soundsPropertyName = "sounds";
    private const string vibrationsPropertyName = "vibrations";

    private const string musicAudioClipsPropertyName = "musicAudioClips";
    
    private SerializedProperty audioEnabledSerializedProperty;
    private SerializedProperty musicEnabledSerializedProperty;
    private SerializedProperty vibrationEnabledSerializedProperty;
```

```
protected override void OnEnable()
{
    base.OnEnable();

    audioEnabledSerializedProperty = serializedObject.FindProperty(audioEnabledPropertyName);
    vibrationEnabledSerializedProperty = serializedObject.FindProperty(vibrationEnabledPropertyName);
    musicEnabledSerializedProperty = serializedObject.FindProperty(musicEnabledPropertyName);

    musicAudioClipsProperty = serializedObject.FindProperty(musicAudioClipsPropertyName);
    
    soundsProperties = serializedObject.FindProperty(soundsPropertyName).GetChildren();
    vibrationsProperties = serializedObject.FindProperty(vibrationsPropertyName).GetChildren();
}
```





![image-20211217112107250](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211217112107250.png)

![image-20211217112122253](C:\Users\xian\AppData\Roaming\Typora\typora-user-images\image-20211217112122253.png)

```
private void DrawToolButton()
{
    GUILayout.BeginHorizontal();
    if (GUILayout.Button("Undo"))
    {
        Undo.PerformUndo();
        GUIUtility.ExitGUI();
    }

    if (GUILayout.Button("Redo"))
    {
        Undo.PerformRedo();
        GUIUtility.ExitGUI();
    }

    // if (GUILayout.Button("Reset"))
    // {
    //     Undo.CollapseUndoOperations(groupId);
    //     Undo.PerformUndo();
    //     GUIUtility.ExitGUI();
    // }
    
    // if (GUILayout.Button("Clear"))
    // {
    //     levelMovableObjectsSerializedProperty.ClearArray();
    //     levelObstaclesSerializedProperty.ClearArray();
    //     selectedLevelSerializedObject.ApplyModifiedProperties();
    // }
    GUILayout.EndHorizontal();
}
```
