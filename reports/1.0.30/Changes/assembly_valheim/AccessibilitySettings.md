# `Valheim.SettingsGui/AccessibilitySettings.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+17/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Initialize() [Method Body Modified]`
- `OnBrightnessChanged() [Method Body Modified]`
- `OnMotionBlurChanged() [Method Body Modified]`
- `OnOkAsync() [Method Body Modified]`
- `OnUIScaleChanged() [Method Body Modified]`
- `public void OnBrightnessChanged()`

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/AccessibilitySettings.cs
+++ b/Valheim.SettingsGui/AccessibilitySettings.cs
@@ -9,12 +9,20 @@
 {
 	private float m_oldGuiScale;
 
+	private float m_oldBrightness;
+
 	[Header("Accessibility")]
 	[SerializeField]
 	private Slider m_guiScaleSlider;
 
 	[SerializeField]
 	private TMP_Text m_guiScaleText;
+
+	[SerializeField]
+	private Slider m_brightnessSlider;
+
+	[SerializeField]
+	private TMP_Text m_brightnessText;
 
 	[SerializeField]
 	private Toggle m_toggleRun;
@@ -57,6 +65,9 @@
 	{
 		m_oldGuiScale = PlatformPrefs.GetFloat("GuiScale", GuiScaler.PlatformDefaultScaling);
 		m_guiScaleSlider.value = m_oldGuiScale * 100f;
+		m_oldBrightness = PlatformPrefs.GetFloat("AccessibilityBrightness");
+		m_brightnessSlider.value = m_oldBrightness * 100f;
+		OnBrightnessChanged();
 		m_toggleRun.isOn = PlatformPrefs.GetInt("ToggleRun", ZInput.IsGamepadActive() ? 1 : 0) == 1;
 		m_immersiveCamera.isOn = PlatformPrefs.GetInt("ShipCameraTilt", 1) == 1;
 		m_cameraShake.isOn = PlatformPrefs.GetInt("CameraShake", 1) == 1;
@@ -74,6 +85,7 @@
 	public void OnOkAsync(OkActionCompletedHandler okActionCompletedCallback)
 	{
 		PlatformPrefs.SetFloat("GuiScale", m_guiScaleSlider.value / 100f);
+		PlatformPrefs.SetFloat("AccessibilityBrightness", m_brightnessSlider.value / 100f);
 		PlatformPrefs.SetInt("ToggleRun", m_toggleRun.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("ShipCameraTilt", m_immersiveCamera.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("CameraShake", m_cameraShake.isOn ? 1 : 0);
@@ -132,6 +144,11 @@
 		GuiScaler.SetScale(m_guiScaleSlider.value / 100f);
 	}
 
+	public void OnBrightnessChanged()
+	{
+		m_brightnessText.text = m_brightnessSlider.value + "%";
+	}
+
 	public void OnMotionBlurChanged()
 	{
 		SharedSettingChanged?.Invoke("MotionBlur", m_motionblurToggle.isOn ? 1 : 0);
```
