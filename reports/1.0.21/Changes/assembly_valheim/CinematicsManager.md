# `CinematicsManager.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Stop() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/CinematicsManager.cs
+++ b/CinematicsManager.cs
@@ -306,6 +306,10 @@
 		{
 			FejdStartup.instance.ResetStartupMusic();
 			FejdStartup.instance.m_mainMenu.SetActive(value: true);
+			if (FejdStartup.instance.m_creditsPanel.activeInHierarchy)
+			{
+				FejdStartup.instance.OnCreditsBack();
+			}
 		}
 	}
 
```
