# `UnityStandardAssets.ImageEffects/NoiseAndScratches.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/NoiseAndScratches.cs
+++ b/UnityStandardAssets.ImageEffects/NoiseAndScratches.cs
@@ -76,16 +76,16 @@
 	{
 		if (!SystemInfo.supportsImageEffects)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 		else if (shaderRGB == null || shaderYUV == null)
 		{
 			Debug.Log("Noise shaders are not set up! Disabling noise effect.");
-			base.enabled = false;
+			enabled = false;
 		}
 		else if (!shaderRGB.isSupported)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 		else if (!shaderYUV.isSupported)
 		{
```
