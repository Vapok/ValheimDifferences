# `UnityStandardAssets.ImageEffects/PostEffectsBase.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/PostEffectsBase.cs
+++ b/UnityStandardAssets.ImageEffects/PostEffectsBase.cs
@@ -24,7 +24,7 @@
 		if (!s)
 		{
 			Debug.Log("Missing shader in " + ToString());
-			base.enabled = false;
+			enabled = false;
 			return null;
 		}
 		if (s.isSupported && (bool)m2Create && m2Create.shader == s)
@@ -156,7 +156,7 @@
 
 	protected void NotSupported()
 	{
-		base.enabled = false;
+		enabled = false;
 		isSupported = false;
 	}
 
```
