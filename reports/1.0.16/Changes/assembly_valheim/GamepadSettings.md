# `Valheim.SettingsGui/GamepadSettings.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/GamepadSettings.cs
+++ b/Valheim.SettingsGui/GamepadSettings.cs
@@ -81,6 +81,9 @@
 	private TMP_Text m_vibrationSliderPercentText;
 
 	[SerializeField]
+	private Toggle m_enableMotionControllsToggle;
+
+	[SerializeField]
 	private GameObject m_motionSensitivityXRoot;
 
 	[SerializeField]
@@ -154,9 +157,11 @@
 
 	private const string GlyphsPlaystation = "Playstation";
 
-	public static float m_motionSensorYAxisSensitivity;
-
-	public static float m_motionSensorXAxisSensitivity;
+	public static bool m_motionControllsEnabled = true;
+
+	public static float m_motionSensorYAxisSensitivity = 0f;
+
+	public static float m_motionSensorXAxisSensitivity = 0f;
 
 	private List<string> m_glyphOptions = new List<string> { "Xbox", "Playstation" };
 
@@ -197,6 +202,7 @@
 		m_originalSliderColor = m_vibrationStrengthSlider.colors.normalColor;
 		m_originalSliderTextColor = m_vibrationSliderLabel.color;
 		PlayerController.m_gamepadSens = PlatformPrefs.GetFloat("GamepadSensitivity", PlayerController.m_gamepadSens);
+		m_motionControllsEnabled = PlatformPrefs.GetInt("MotionControlls", 1) == 1;
 		m_motionSensorYAxisSensitivity = PlatformPrefs.GetFloat("MotionSensorYAxisSensitivity", m_motionSensorYAxisSensitivity);
 		m_motionSensorXAxisSensitivity = PlatformPrefs.GetFloat("MotionSensorXAxisSensitivity", m_motionSensorXAxisSensitivity);
 		PlayerController.m_invertCameraY = PlatformPrefs.GetInt("InvertCameraY", PlatformPrefs.GetInt("InvertMouse")) == 1;
@@ -230,6 +236,7 @@
 		m_vibrationSliderPercentText.text = Mathf.Round(m_vibrationStrengthSlider.value * 100f) + "%";
 		m_useAdaptiveTriggers.isOn = PlatformPrefs.GetInt("GamepadAdaptiveTriggers", 1) == 1;
 		m_controllerSpeakerSlider.value = PlatformPrefs.GetFloat("GamepadSpeakerVolume", 1f);
+		m_enableMotionControllsToggle.isOn = m_motionControllsEnabled;
 		m_motionSensitivityXAxisSlider.value = Mathf.Abs(m_motionSensorXAxisSensitivity * 10f);
 		m_motionSensitivityXAxisPercentText.text = Math.Round(m_motionSensitivityXAxisSlider.value / 10f, 1).ToString();
 		m_motionSensitivityYAxisSlider.value = Mathf.Abs(m_motionSensorYAxisSensitivity * 10f);
@@ -261,6 +268,8 @@
 		PlatformPrefs.SetInt("SwapTriggers", m_swapTriggers.isOn ? 1 : 0);
 		PlatformPrefs.SetFloat("GamepadVibrationStrength", m_vibrationStrengthSlider.value);
 		PlatformPrefs.SetInt("GamepadAdaptiveTriggers", m_useAdaptiveTriggers.isOn ? 1 : 0);
+		m_motionControllsEnabled = m_enableMotionControllsToggle.isOn;
+		PlatformPrefs.SetInt("MotionControlls", m_motionControllsEnabled ? 1 : 0);
 		m_motionSensorXAxisSensitivity = (float)((!m_controllerInvertCameraX.isOn) ? 1 : (-1)) * m_motionSensitivityXAxisSlider.value / 10f;
 		m_motionSensorYAxisSensitivity = (float)((!m_controllerInvertCameraY.isOn) ? 1 : (-1)) * m_motionSensitivityYAxisSlider.value / 10f;
 		PlatformPrefs.SetFloat("MotionSensorXAxisSensitivity", m_motionSensorXAxisSensitivity);
```
