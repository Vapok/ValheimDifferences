# `UnityStandardAssets.ImageEffects/Grayscale.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/Grayscale.cs
+++ b/UnityStandardAssets.ImageEffects/Grayscale.cs
@@ -13,8 +13,8 @@
 
 	private void OnRenderImage(RenderTexture source, RenderTexture destination)
 	{
-		base.material.SetTexture("_RampTex", textureRamp);
-		base.material.SetFloat("_RampOffset", rampOffset);
-		Graphics.Blit(source, destination, base.material);
+		material.SetTexture("_RampTex", textureRamp);
+		material.SetFloat("_RampOffset", rampOffset);
+		Graphics.Blit(source, destination, material);
 	}
 }
```
