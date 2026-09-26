# `GoogleAnalyticsV4.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_googleanalytics.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GoogleAnalyticsV4.cs
+++ b/GoogleAnalyticsV4.cs
@@ -90,7 +90,7 @@
 	{
 		if (initialized)
 		{
-			Object.DestroyImmediate(base.gameObject);
+			Object.DestroyImmediate(gameObject);
 			return;
 		}
 		InitializeTracker();
```
