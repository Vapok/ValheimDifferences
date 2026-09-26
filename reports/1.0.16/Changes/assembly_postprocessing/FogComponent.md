# `UnityEngine.PostProcessing/FogComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/FogComponent.cs
+++ b/UnityEngine.PostProcessing/FogComponent.cs
@@ -35,7 +35,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && context.isGBufferAvailable && RenderSettings.fog)
+			if (model.enabled && context.isGBufferAvailable && RenderSettings.fog)
 			{
 				return !context.interrupted;
 			}
@@ -60,7 +60,7 @@
 
 	public override void PopulateCommandBuffer(CommandBuffer cb)
 	{
-		FogModel.Settings settings = base.model.settings;
+		FogModel.Settings settings = model.settings;
 		Material material = context.materialFactory.Get("Hidden/Post FX/Fog");
 		material.shaderKeywords = null;
 		Color value = (GraphicsUtils.isLinearColorSpace ? RenderSettings.fogColor.linear : RenderSettings.fogColor);
```
