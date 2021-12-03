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
