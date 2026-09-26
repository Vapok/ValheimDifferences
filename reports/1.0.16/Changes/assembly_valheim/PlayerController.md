# `PlayerController.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlayerController.cs
+++ b/PlayerController.cs
@@ -57,7 +57,7 @@
 		m_nview = GetComponent<ZNetView>();
 		if (m_nview.GetZDO() == null)
 		{
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		KeyboardMouseSettings.SetPlatformSpecificFirstTimeSettings();
@@ -67,6 +67,7 @@
 		m_invertMouse = PlatformPrefs.GetInt("InvertMouse") == 1;
 		m_invertCameraY = PlatformPrefs.GetInt("InvertCameraY", m_invertMouse ? 1 : 0) == 1;
 		m_invertCameraX = PlatformPrefs.GetInt("InvertCameraX") == 1;
+		GamepadSettings.m_motionControllsEnabled = PlatformPrefs.GetInt("MotionControlls", 1) == 1;
 		GamepadSettings.m_motionSensorXAxisSensitivity = PlatformPrefs.GetFloat("MotionSensorXAxisSensitivity", GamepadSettings.m_motionSensorXAxisSensitivity);
 		GamepadSettings.m_motionSensorYAxisSensitivity = PlatformPrefs.GetFloat("MotionSensorYAxisSensitivity", GamepadSettings.m_motionSensorYAxisSensitivity);
 	}
@@ -206,7 +207,7 @@
 
 	private void ToggleMotionSensor()
 	{
-		if (GamepadSettings.m_motionSensorYAxisSensitivity == 0f && GamepadSettings.m_motionSensorXAxisSensitivity == 0f)
+		if (!GamepadSettings.m_motionControllsEnabled)
 		{
 			m_motionSensorActive = false;
 			MessageHud.instance.ShowMessage(MessageHud.MessageType.TopLeft, Localization.instance.Localize(Utils.GetPlatformSpecificLocalizationKey("$settings_controller_motion_sensor_settings_off", localizeSwitch: true, localizePlayStation: true, localizeXbox: false)));
```
