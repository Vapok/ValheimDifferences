# `Valheim.SettingsGui/GameplaySettings.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/GameplaySettings.cs
+++ b/Valheim.SettingsGui/GameplaySettings.cs
@@ -185,7 +185,7 @@
 			UnifiedPopup.Push(new WarningPopup("", "$settings_deleteplayfabaccount_ingamewarning", UnifiedPopup.Pop));
 			return;
 		}
-		UnifiedPopup.Push(new YesNoPopup("$settings_deleteplayfabaccount", "$settings_deleteplayfabaccount_text", delegate
+		UnifiedPopup.Push(new YesNoPopup("$settings_deleteplayfabaccount", "$settings_deleteplayfabaccount_text", () =>
 		{
 			UnifiedPopup.Pop();
 			PlayFabManager.instance.DeletePlayerTitleAccount();
@@ -196,7 +196,7 @@
 	{
 		if (m_blockedPlayerListInstance == null)
 		{
-			m_blockedPlayerListInstance = UnityEngine.Object.Instantiate(m_playerListPrefab, base.transform);
+			m_blockedPlayerListInstance = UnityEngine.Object.Instantiate(m_playerListPrefab, transform);
 		}
 		else
 		{
```
