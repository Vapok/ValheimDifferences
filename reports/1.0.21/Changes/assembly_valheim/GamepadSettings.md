# `Valheim.SettingsGui/GamepadSettings.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Initialize() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/GamepadSettings.cs
+++ b/Valheim.SettingsGui/GamepadSettings.cs
@@ -157,11 +157,11 @@
 
 	private const string GlyphsPlaystation = "Playstation";
 
-	public static bool m_motionControllsEnabled = true;
-
-	public static float m_motionSensorYAxisSensitivity = 0f;
-
-	public static float m_motionSensorXAxisSensitivity = 0f;
+	public static bool m_motionControllsEnabled = false;
+
+	public static float m_motionSensorYAxisSensitivity = 1f;
+
+	public static float m_motionSensorXAxisSensitivity = 1f;
 
 	private List<string> m_glyphOptions = new List<string> { "Xbox", "Playstation" };
 
@@ -202,7 +202,7 @@
 		m_originalSliderColor = m_vibrationStrengthSlider.colors.normalColor;
 		m_originalSliderTextColor = m_vibrationSliderLabel.color;
 		PlayerController.m_gamepadSens = PlatformPrefs.GetFloat("GamepadSensitivity", PlayerController.m_gamepadSens);
-		m_motionControllsEnabled = PlatformPrefs.GetInt("MotionControlls", 1) == 1;
+		m_motionControllsEnabled = PlatformPrefs.GetInt("MotionControlls", m_motionControllsEnabled ? 1 : 0) == 1;
 		m_motionSensorYAxisSensitivity = PlatformPrefs.GetFloat("MotionSensorYAxisSensitivity", m_motionSensorYAxisSensitivity);
 		m_motionSensorXAxisSensitivity = PlatformPrefs.GetFloat("MotionSensorXAxisSensitivity", m_motionSensorXAxisSensitivity);
 		PlayerController.m_invertCameraY = PlatformPrefs.GetInt("InvertCameraY", PlatformPrefs.GetInt("InvertMouse")) == 1;
```
