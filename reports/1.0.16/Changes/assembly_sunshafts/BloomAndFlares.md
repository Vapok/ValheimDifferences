# `UnityStandardAssets.ImageEffects/BloomAndFlares.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/BloomAndFlares.cs
+++ b/UnityStandardAssets.ImageEffects/BloomAndFlares.cs
@@ -120,7 +120,7 @@
 		RenderTexture temporary3 = RenderTexture.GetTemporary(source.width / 4, source.height / 4, 0, format);
 		RenderTexture temporary4 = RenderTexture.GetTemporary(source.width / 4, source.height / 4, 0, format);
 		float num = 1f * (float)source.width / (1f * (float)source.height);
-		float num2 = 0.001953125f;
+		float num2 = 2f / 1024f;
 		Graphics.Blit(source, temporary, screenBlend, 2);
 		Graphics.Blit(temporary, temporary2, screenBlend, 2);
 		RenderTexture.ReleaseTemporary(temporary);
@@ -134,9 +134,9 @@
 		{
 			float num3 = (1f + (float)i * 0.5f) * sepBlurSpread;
 			separableBlurMaterial.SetVector("offsets", new Vector4(0f, num3 * num2, 0f, 0f));
-			RenderTexture obj = ((i == 0) ? temporary3 : temporary2);
-			Graphics.Blit(obj, temporary4, separableBlurMaterial);
-			obj.DiscardContents();
+			RenderTexture renderTexture = ((i == 0) ? temporary3 : temporary2);
+			Graphics.Blit(renderTexture, temporary4, separableBlurMaterial);
+			renderTexture.DiscardContents();
 			separableBlurMaterial.SetVector("offsets", new Vector4(num3 / num * num2, 0f, 0f, 0f));
 			Graphics.Blit(temporary4, temporary2, separableBlurMaterial);
 			temporary4.DiscardContents();
```
