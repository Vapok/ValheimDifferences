# `AmplifyOcclusionEffect.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/AmplifyOcclusionEffect.cs
+++ b/AmplifyOcclusionEffect.cs
@@ -381,7 +381,7 @@
 		if (!checkRenderTextureFormats())
 		{
 			Debug.LogError("[AmplifyOcclusion] Target platform does not meet the minimum requirements for this effect to work properly.");
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		if (CacheAware)
```
