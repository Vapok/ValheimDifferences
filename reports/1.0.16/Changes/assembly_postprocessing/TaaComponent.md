# `UnityEngine.PostProcessing/TaaComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/TaaComponent.cs
+++ b/UnityEngine.PostProcessing/TaaComponent.cs
@@ -33,7 +33,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && base.model.settings.method == AntialiasingModel.Method.Taa && SystemInfo.supportsMotionVectors && SystemInfo.supportedRenderTargetCount >= 2)
+			if (model.enabled && model.settings.method == AntialiasingModel.Method.Taa && SystemInfo.supportsMotionVectors && SystemInfo.supportedRenderTargetCount >= 2)
 			{
 				return !context.interrupted;
 			}
@@ -55,7 +55,7 @@
 
 	public void SetProjectionMatrix(Func<Vector2, Matrix4x4> jitteredFunc)
 	{
-		AntialiasingModel.TaaSettings taaSettings = base.model.settings.taaSettings;
+		AntialiasingModel.TaaSettings taaSettings = model.settings.taaSettings;
 		Vector2 vector = GenerateRandomOffset();
 		vector *= taaSettings.jitterSpread;
 		context.camera.nonJitteredProjectionMatrix = context.camera.projectionMatrix;
@@ -78,7 +78,7 @@
 	{
 		Material material = context.materialFactory.Get("Hidden/Post FX/Temporal Anti-aliasing");
 		material.shaderKeywords = null;
-		AntialiasingModel.TaaSettings taaSettings = base.model.settings.taaSettings;
+		AntialiasingModel.TaaSettings taaSettings = model.settings.taaSettings;
 		if (m_ResetHistory || m_HistoryTexture == null || m_HistoryTexture.width != source.width || m_HistoryTexture.height != source.height)
 		{
 			if ((bool)m_HistoryTexture)
```
