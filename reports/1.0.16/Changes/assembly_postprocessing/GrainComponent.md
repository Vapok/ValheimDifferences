# `UnityEngine.PostProcessing/GrainComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/GrainComponent.cs
+++ b/UnityEngine.PostProcessing/GrainComponent.cs
@@ -19,7 +19,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && base.model.settings.intensity > 0f && SystemInfo.SupportsRenderTextureFormat(RenderTextureFormat.ARGBHalf))
+			if (model.enabled && model.settings.intensity > 0f && SystemInfo.SupportsRenderTextureFormat(RenderTextureFormat.ARGBHalf))
 			{
 				return !context.interrupted;
 			}
@@ -35,7 +35,7 @@
 
 	public override void Prepare(Material uberMaterial)
 	{
-		GrainModel.Settings settings = base.model.settings;
+		GrainModel.Settings settings = model.settings;
 		uberMaterial.EnableKeyword("GRAIN");
 		float realtimeSinceStartup = Time.realtimeSinceStartup;
 		float value = Random.value;
```
