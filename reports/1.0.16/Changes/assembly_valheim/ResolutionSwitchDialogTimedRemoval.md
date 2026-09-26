# `Valheim.SettingsGui/ResolutionSwitchDialogTimedRemoval.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/ResolutionSwitchDialogTimedRemoval.cs
+++ b/Valheim.SettingsGui/ResolutionSwitchDialogTimedRemoval.cs
@@ -32,7 +32,7 @@
 		if (m_resCountdownTimer <= 0f || ZInput.GetButtonDown("JoyBack") || ZInput.GetButtonDown("JoyButtonB") || ZInput.GetKeyDown(KeyCode.Escape))
 		{
 			m_graphicsSettings.RevertMode();
-			base.gameObject.SetActive(value: false);
+			gameObject.SetActive(value: false);
 		}
 	}
 }
```
