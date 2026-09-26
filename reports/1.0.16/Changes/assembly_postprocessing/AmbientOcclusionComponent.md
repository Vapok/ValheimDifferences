# `UnityEngine.PostProcessing/AmbientOcclusionComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/AmbientOcclusionComponent.cs
+++ b/UnityEngine.PostProcessing/AmbientOcclusionComponent.cs
@@ -52,11 +52,11 @@
 	{
 		get
 		{
-			if (context.isGBufferAvailable && !base.model.settings.forceForwardCompatibility)
+			if (context.isGBufferAvailable && !model.settings.forceForwardCompatibility)
 			{
 				return OcclusionSource.GBuffer;
 			}
-			if (base.model.settings.highPrecision && (!context.isGBufferAvailable || base.model.settings.forceForwardCompatibility))
+			if (model.settings.highPrecision && (!context.isGBufferAvailable || model.settings.forceForwardCompatibility))
 			{
 				return OcclusionSource.DepthTexture;
 			}
@@ -68,9 +68,9 @@
 	{
 		get
 		{
-			if (context.isHdr && base.model.settings.ambientOnly && context.isGBufferAvailable)
+			if (context.isHdr && model.settings.ambientOnly && context.isGBufferAvailable)
 			{
-				return !base.model.settings.forceForwardCompatibility;
+				return !model.settings.forceForwardCompatibility;
 			}
 			return false;
 		}
@@ -80,7 +80,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && base.model.settings.intensity > 0f)
+			if (model.enabled && model.settings.intensity > 0f)
 			{
 				return !context.interrupted;
 			}
@@ -118,7 +118,7 @@
 
 	public override void PopulateCommandBuffer(CommandBuffer cb)
 	{
-		AmbientOcclusionModel.Settings settings = base.model.settings;
+		AmbientOcclusionModel.Settings settings = model.settings;
 		Material mat = context.materialFactory.Get("Hidden/Post FX/Blit");
 		Material material = context.materialFactory.Get("Hidden/Post FX/Ambient Occlusion");
 		material.shaderKeywords = null;
```
