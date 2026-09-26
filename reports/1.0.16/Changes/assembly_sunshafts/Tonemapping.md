# `UnityStandardAssets.ImageEffects/Tonemapping.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/Tonemapping.cs
+++ b/UnityStandardAssets.ImageEffects/Tonemapping.cs
@@ -86,7 +86,7 @@
 			{
 				num = remapCurve[remapCurve.length - 1].time;
 			}
-			for (float num2 = 0f; num2 <= 1f; num2 += 0.003921569f)
+			for (float num2 = 0f; num2 <= 1f; num2 += 1f / 255f)
 			{
 				float num3 = remapCurve.Evaluate(num2 * 1f * num);
 				curveTex.SetPixel((int)Mathf.Floor(num2 * 255f), 0, new Color(num3, num3, num3));
```
