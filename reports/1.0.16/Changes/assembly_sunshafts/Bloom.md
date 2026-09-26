# `UnityStandardAssets.ImageEffects/Bloom.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/Bloom.cs
+++ b/UnityStandardAssets.ImageEffects/Bloom.cs
@@ -141,7 +141,7 @@
 		int width2 = source.width / 4;
 		int height2 = source.height / 4;
 		float num = 1f * (float)source.width / (1f * (float)source.height);
-		float num2 = 0.001953125f;
+		float num2 = 2f / 1024f;
 		RenderTexture temporary = RenderTexture.GetTemporary(width2, height2, 0, format);
 		RenderTexture temporary2 = RenderTexture.GetTemporary(width, height, 0, format);
 		if (quality > BloomQuality.Cheap)
```
