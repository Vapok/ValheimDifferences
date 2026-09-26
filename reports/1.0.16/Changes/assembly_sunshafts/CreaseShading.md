# `UnityStandardAssets.ImageEffects/CreaseShading.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/CreaseShading.cs
+++ b/UnityStandardAssets.ImageEffects/CreaseShading.cs
@@ -48,7 +48,7 @@
 		int width = source.width;
 		int height = source.height;
 		float num = 1f * (float)width / (1f * (float)height);
-		float num2 = 0.001953125f;
+		float num2 = 2f / 1024f;
 		RenderTexture temporary = RenderTexture.GetTemporary(width, height, 0);
 		RenderTexture renderTexture = RenderTexture.GetTemporary(width / 2, height / 2, 0);
 		Graphics.Blit(source, temporary, depthFetchMaterial);
```
