# `Valheim.SettingsGui/GameplaySettings.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/GameplaySettings.cs
+++ b/Valheim.SettingsGui/GameplaySettings.cs
@@ -43,6 +43,9 @@
 
 	[SerializeField]
 	private Toggle m_showBuildPieceAuthor;
+
+	[SerializeField]
+	private Toggle m_skipIntroCinematic;
 
 	[SerializeField]
 	private Slider m_autoBackups;
@@ -101,6 +104,7 @@
 		m_reduceBGUsage.isOn = PlatformPrefs.GetInt("ReduceBackgroundUsage") == 1;
 		m_enableConsole.isOn = PlatformPrefs.GetInt("EnableConsole", Console.instance.IsConsoleEnabled() ? 1 : 0) == 1;
 		m_showBuildPieceAuthor.isOn = PlatformPrefs.GetInt("ShowBuildPieceAuthor", (Application.platform == RuntimePlatform.PS5) ? 1 : 0) == 1;
+		m_skipIntroCinematic.isOn = PlatformPrefs.GetBool("SkipIntroCinematic");
 		Hud.s_showBuildPieceAuthor = m_showBuildPieceAuthor.isOn;
 		m_autoBackups.value = PlatformPrefs.GetInt("AutoBackups", 4);
 		UpdateLanguageText();
@@ -119,6 +123,7 @@
 		PlatformPrefs.SetInt("ReduceBackgroundUsage", m_reduceBGUsage.isOn ? 1 : 0);
 		PlatformPrefs.SetInt("AutoBackups", (int)m_autoBackups.value);
 		PlatformPrefs.SetInt("ShowBuildPieceAuthor", m_showBuildPieceAuthor.isOn ? 1 : 0);
+		PlatformPrefs.SetBool("SkipIntroCinematic", m_skipIntroCinematic.isOn);
 		Hud.s_showBuildPieceAuthor = m_showBuildPieceAuthor.isOn;
 		ZInput.ToggleRun = m_toggleRun.isOn;
 		Raven.m_tutorialsEnabled = m_tutorialsEnabled.isOn;
@@ -154,7 +159,6 @@
 	public void OnConsoleToggle()
 	{
 		PlatformPrefs.SetInt("EnableConsole", m_enableConsole.isOn ? 1 : 0);
-		UnityEngine.Object.FindAnyObjectByType<KeyboardMouseSettings>(FindObjectsInactive.Include).SetConsoleEnabled(m_enableConsole.isOn);
 		Console.SetConsoleEnabled(m_enableConsole.isOn);
 	}
 
```
