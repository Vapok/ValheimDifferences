# `HideWhenRunning.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/HideWhenRunning.cs
+++ b/HideWhenRunning.cs
@@ -6,7 +6,7 @@
 	{
 		if (Application.isPlaying)
 		{
-			base.gameObject.SetActive(value: false);
+			gameObject.SetActive(value: false);
 		}
 	}
 }
```
