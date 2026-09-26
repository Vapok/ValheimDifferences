# `UnityStandardAssets.ImageEffects/ImageEffectBase.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/ImageEffectBase.cs
+++ b/UnityStandardAssets.ImageEffects/ImageEffectBase.cs
@@ -27,11 +27,11 @@
 	{
 		if (!SystemInfo.supportsImageEffects)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 		else if (!shader || !shader.isSupported)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 	}
 
```
