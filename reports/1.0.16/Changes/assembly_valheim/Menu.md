# `Menu.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Menu.cs
+++ b/Menu.cs
@@ -351,7 +351,7 @@
 			{
 				m_closeMenuState = CloseMenuState.CanBeClosed;
 			}
-			if (ZInput.IsExclusiveGamepadActive() && base.gameObject.activeInHierarchy && EventSystem.current.currentSelectedGameObject == null && m_firstMenuButton != null)
+			if (ZInput.IsExclusiveGamepadActive() && gameObject.activeInHierarchy && EventSystem.current.currentSelectedGameObject == null && m_firstMenuButton != null)
 			{
 				StartCoroutine(SelectEntry(m_firstMenuButton.gameObject));
 			}
@@ -393,7 +393,7 @@
 		}
 		if (m_updateLocalizationTimer > 30)
 		{
-			Localization.instance.ReLocalizeVisible(base.transform);
+			Localization.instance.ReLocalizeVisible(transform);
 			m_updateLocalizationTimer = 0;
 		}
 		else
@@ -411,7 +411,7 @@
 	public void OnSettings()
 	{
 		Gogan.LogEvent("Screen", "Enter", "Settings", 0L);
-		m_settingsInstance = UnityEngine.Object.Instantiate(m_settingsPrefab, base.transform);
+		m_settingsInstance = UnityEngine.Object.Instantiate(m_settingsPrefab, transform);
 		m_closeMenuState = CloseMenuState.SettingsOpen;
 	}
 
@@ -425,7 +425,7 @@
 	{
 		if (m_currentPlayersInstance == null)
 		{
-			m_currentPlayersInstance = UnityEngine.Object.Instantiate(CurrentPlayersPrefab, base.transform);
+			m_currentPlayersInstance = UnityEngine.Object.Instantiate(CurrentPlayersPrefab, transform);
 		}
 		else
 		{
@@ -498,7 +498,7 @@
 
 	public void OnQuitYes()
 	{
-		ZNet.instance.EnoughDiskSpaceAvailable(out var exitGamePopupShown, exitGamePrompt: true, delegate(bool exit)
+		ZNet.instance.EnoughDiskSpaceAvailable(out var exitGamePopupShown, exitGamePrompt: true, (bool exit) =>
 		{
 			if (exit)
 			{
@@ -579,7 +579,7 @@
 
 	public void OnButtonFeedback()
 	{
-		UnityEngine.Object.Instantiate(m_feedbackPrefab, base.transform);
+		UnityEngine.Object.Instantiate(m_feedbackPrefab, transform);
 	}
 
 	public void ShowCloudStorageFullWarning(CloudStorageFullOkCallback okCallback)
```
