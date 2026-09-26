# `UnityEngine.PostProcessing/BloomComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/BloomComponent.cs
+++ b/UnityEngine.PostProcessing/BloomComponent.cs
@@ -35,7 +35,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && base.model.settings.bloom.intensity > 0f)
+			if (model.enabled && model.settings.bloom.intensity > 0f)
 			{
 				return !context.interrupted;
 			}
@@ -45,8 +45,8 @@
 
 	public void Prepare(RenderTexture source, Material uberMaterial, Texture autoExposure)
 	{
-		BloomModel.BloomSettings bloom = base.model.settings.bloom;
-		BloomModel.LensDirtSettings lensDirt = base.model.settings.lensDirt;
+		BloomModel.BloomSettings bloom = model.settings.bloom;
+		BloomModel.LensDirtSettings lensDirt = model.settings.lensDirt;
 		Material material = context.materialFactory.Get("Hidden/Post FX/Bloom");
 		material.shaderKeywords = null;
 		material.SetTexture(Uniforms._AutoExposure, autoExposure);
```
