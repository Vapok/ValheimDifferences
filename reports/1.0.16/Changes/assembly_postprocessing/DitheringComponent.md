# `UnityEngine.PostProcessing/DitheringComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/DitheringComponent.cs
+++ b/UnityEngine.PostProcessing/DitheringComponent.cs
@@ -19,7 +19,7 @@
 	{
 		get
 		{
-			if (base.model.enabled)
+			if (model.enabled)
 			{
 				return !context.interrupted;
 			}
```
