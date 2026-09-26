# `UnityStandardAssets.ImageEffects/ColorCorrectionRamp.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_sunshafts.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityStandardAssets.ImageEffects/ColorCorrectionRamp.cs
+++ b/UnityStandardAssets.ImageEffects/ColorCorrectionRamp.cs
@@ -10,7 +10,7 @@
 
 	private void OnRenderImage(RenderTexture source, RenderTexture destination)
 	{
-		base.material.SetTexture("_RampTex", textureRamp);
-		Graphics.Blit(source, destination, base.material);
+		material.SetTexture("_RampTex", textureRamp);
+		Graphics.Blit(source, destination, material);
 	}
 }
```
