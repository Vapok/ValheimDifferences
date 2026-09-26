# `UnityStandardAssets.ImageEffects/Blur.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/Blur.cs
+++ b/UnityStandardAssets.ImageEffects/Blur.cs
@@ -41,11 +41,11 @@
 	{
 		if (!SystemInfo.supportsImageEffects)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 		else if (!blurShader || !material.shader.isSupported)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 	}
 
```
