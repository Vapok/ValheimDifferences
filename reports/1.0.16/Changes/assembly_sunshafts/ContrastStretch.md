# `UnityStandardAssets.ImageEffects/ContrastStretch.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/ContrastStretch.cs
+++ b/UnityStandardAssets.ImageEffects/ContrastStretch.cs
@@ -91,11 +91,11 @@
 	{
 		if (!SystemInfo.supportsImageEffects)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 		else if (!shaderAdapt.isSupported || !shaderApply.isSupported || !shaderLum.isSupported || !shaderReduce.isSupported)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 	}
 
```
