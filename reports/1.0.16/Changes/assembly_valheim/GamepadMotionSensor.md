# `GamepadMotionSensor.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GamepadMotionSensor.cs
+++ b/GamepadMotionSensor.cs
@@ -9,7 +9,7 @@
 
 	public static void ToggleMotionSensor()
 	{
-		if (GamepadSettings.m_motionSensorYAxisSensitivity == 0f && GamepadSettings.m_motionSensorXAxisSensitivity == 0f)
+		if (!GamepadSettings.m_motionControllsEnabled)
 		{
 			m_motionSensorActive = false;
 			MessageHud.instance.ShowMessage(MessageHud.MessageType.TopLeft, Localization.instance.Localize(Utils.GetPlatformSpecificLocalizationKey("$settings_controller_motion_sensor_settings_off", localizeSwitch: true, localizePlayStation: true, localizeXbox: false)), 0, null, showDespiteHiddenHUD: false, log: false);
```
