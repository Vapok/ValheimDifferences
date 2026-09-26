# `UnityStandardAssets.ImageEffects/ColorCorrectionCurves.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/ColorCorrectionCurves.cs
+++ b/UnityStandardAssets.ImageEffects/ColorCorrectionCurves.cs
@@ -106,7 +106,7 @@
 		CheckResources();
 		if (redChannel != null && greenChannel != null && blueChannel != null)
 		{
-			for (float num = 0f; num <= 1f; num += 0.003921569f)
+			for (float num = 0f; num <= 1f; num += 1f / 255f)
 			{
 				float num2 = Mathf.Clamp(redChannel.Evaluate(num), 0f, 1f);
 				float num3 = Mathf.Clamp(greenChannel.Evaluate(num), 0f, 1f);
```
