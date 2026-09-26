# `UnityEngine.PostProcessing/MotionBlurComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/MotionBlurComponent.cs
+++ b/UnityEngine.PostProcessing/MotionBlurComponent.cs
@@ -343,8 +343,8 @@
 	{
 		get
 		{
-			MotionBlurModel.Settings settings = base.model.settings;
-			if (base.model.enabled && ((settings.shutterAngle > 0f && reconstructionFilter.IsSupported()) || settings.frameBlending > 0f) && SystemInfo.graphicsDeviceType != GraphicsDeviceType.OpenGLES2)
+			MotionBlurModel.Settings settings = model.settings;
+			if (model.enabled && ((settings.shutterAngle > 0f && reconstructionFilter.IsSupported()) || settings.frameBlending > 0f) && SystemInfo.graphicsDeviceType != GraphicsDeviceType.OpenGLES2)
 			{
 				return !context.interrupted;
 			}
@@ -390,7 +390,7 @@
 		}
 		Material material = context.materialFactory.Get("Hidden/Post FX/Motion Blur");
 		Material mat = context.materialFactory.Get("Hidden/Post FX/Blit");
-		MotionBlurModel.Settings settings = base.model.settings;
+		MotionBlurModel.Settings settings = model.settings;
 		RenderTextureFormat format = (context.isHdr ? RenderTextureFormat.DefaultHDR : RenderTextureFormat.Default);
 		int tempRT = Uniforms._TempRT;
 		cb.GetTemporaryRT(tempRT, context.width, context.height, 0, FilterMode.Point, format);
```
