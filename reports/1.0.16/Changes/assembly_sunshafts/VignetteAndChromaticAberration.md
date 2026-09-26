# `UnityStandardAssets.ImageEffects/VignetteAndChromaticAberration.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/VignetteAndChromaticAberration.cs
+++ b/UnityStandardAssets.ImageEffects/VignetteAndChromaticAberration.cs
@@ -76,11 +76,11 @@
 				Graphics.Blit(source, renderTexture2, m_ChromAberrationMaterial, 0);
 				for (int i = 0; i < 2; i++)
 				{
-					m_SeparableBlurMaterial.SetVector("offsets", new Vector4(0f, blurSpread * 0.001953125f, 0f, 0f));
+					m_SeparableBlurMaterial.SetVector("offsets", new Vector4(0f, blurSpread * (2f / 1024f), 0f, 0f));
 					RenderTexture temporary = RenderTexture.GetTemporary(width / 2, height / 2, 0, source.format);
 					Graphics.Blit(renderTexture2, temporary, m_SeparableBlurMaterial);
 					RenderTexture.ReleaseTemporary(renderTexture2);
-					m_SeparableBlurMaterial.SetVector("offsets", new Vector4(blurSpread * 0.001953125f / num, 0f, 0f, 0f));
+					m_SeparableBlurMaterial.SetVector("offsets", new Vector4(blurSpread * (2f / 1024f) / num, 0f, 0f, 0f));
 					renderTexture2 = RenderTexture.GetTemporary(width / 2, height / 2, 0, source.format);
 					Graphics.Blit(temporary, renderTexture2, m_SeparableBlurMaterial);
 					RenderTexture.ReleaseTemporary(temporary);
```
