# `Valheim.SettingsGui/AccessibilitySettings.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/AccessibilitySettings.cs
+++ b/Valheim.SettingsGui/AccessibilitySettings.cs
@@ -40,14 +40,17 @@
 	[SerializeField]
 	private Toggle m_soundIndicatorsToggle;
 
+	[SerializeField]
+	private Toggle m_toggleBlockToggle;
+
 	public event Action<string, int> SharedSettingChanged;
 
 	public void OnTabOpen(Button backButton, Button okButton)
 	{
-		GuiUtils.SetNavigationDown(m_motionblurToggle, backButton);
-		GuiUtils.SetNavigationUp(backButton, m_motionblurToggle);
-		GuiUtils.SetNavigationUp(okButton, m_depthOfFieldToggle);
-		GuiUtils.SetNavigationDown(m_depthOfFieldToggle, okButton);
+		GuiUtils.SetNavigationDown(m_depthOfFieldToggle, backButton);
+		GuiUtils.SetNavigationUp(backButton, m_depthOfFieldToggle);
+		GuiUtils.SetNavigationUp(okButton, m_toggleBlockToggle);
+		GuiUtils.SetNavigationDown(m_toggleBlockToggle, okButton);
 	}
 
 	public void Initialize()
@@ -62,6 +65,7 @@
 		m_depthOfFieldToggle.isOn = PlatformPrefs.GetInt("DOF", 1) == 1;
 		m_closedCaptionsToggle.isOn = PlatformPrefs.GetInt("ClosedCaptions") == 1;
 		m_soundIndicatorsToggle.isOn = PlatformPrefs.GetInt("DirectionalSoundIndicators") == 1;
+		m_toggleBlockToggle.isOn = PlatformPrefs.GetInt("ToggleBlock") == 1;
 		Settings.ReduceFlashingLights = m_reduceFlashingLights.isOn;
 		Settings.DirectionalSoundIndicators = m_soundIndicatorsToggle.isOn;
 		Settings.ClosedCaptions = m_closedCaptionsToggle.isOn;
@@ -76,9 +80,14 @@
 		PlatformPrefs.SetInt("ReduceFlashingLights", m_reduceFlashingLights.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("ClosedCaptions", m_closedCaptionsToggle.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("DirectionalSoundIndicators", m_soundIndicatorsToggle.isOn ? 1 : 0);
+		PlatformPrefs.SetInt("ToggleBlock", m_toggleBlockToggle.isOn ? 1 : 0);
 		Settings.ReduceFlashingLights = m_reduceFlashingLights.isOn;
 		Settings.ClosedCaptions = m_closedCaptionsToggle.isOn;
 		Settings.DirectionalSoundIndicators = m_soundIndicatorsToggle.isOn;
+		if (Player.m_localPlayer != null)
+		{
+			Player.m_localPlayer.ToggleBlock = m_toggleBlockToggle.isOn;
+		}
 		okActionCompletedCallback?.Invoke();
 	}
 
```
