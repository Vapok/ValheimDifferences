# `UnityEngine.PostProcessing/BuiltinDebugViewsComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/BuiltinDebugViewsComponent.cs
+++ b/UnityEngine.PostProcessing/BuiltinDebugViewsComponent.cs
@@ -97,9 +97,9 @@
 	{
 		get
 		{
-			if (!base.model.IsModeActive(BuiltinDebugViewsModel.Mode.Depth) && !base.model.IsModeActive(BuiltinDebugViewsModel.Mode.Normals))
-			{
-				return base.model.IsModeActive(BuiltinDebugViewsModel.Mode.MotionVectors);
+			if (!model.IsModeActive(BuiltinDebugViewsModel.Mode.Depth) && !model.IsModeActive(BuiltinDebugViewsModel.Mode.Normals))
+			{
+				return model.IsModeActive(BuiltinDebugViewsModel.Mode.MotionVectors);
 			}
 			return true;
 		}
@@ -107,7 +107,7 @@
 
 	public override DepthTextureMode GetCameraFlags()
 	{
-		BuiltinDebugViewsModel.Mode mode = base.model.settings.mode;
+		BuiltinDebugViewsModel.Mode mode = model.settings.mode;
 		DepthTextureMode depthTextureMode = DepthTextureMode.None;
 		switch (mode)
 		{
@@ -126,7 +126,7 @@
 
 	public override CameraEvent GetCameraEvent()
 	{
-		if (base.model.settings.mode != BuiltinDebugViewsModel.Mode.MotionVectors)
+		if (model.settings.mode != BuiltinDebugViewsModel.Mode.MotionVectors)
 		{
 			return CameraEvent.BeforeImageEffectsOpaque;
 		}
@@ -140,7 +140,7 @@
 
 	public override void PopulateCommandBuffer(CommandBuffer cb)
 	{
-		BuiltinDebugViewsModel.Settings settings = base.model.settings;
+		BuiltinDebugViewsModel.Settings settings = model.settings;
 		Material material = context.materialFactory.Get("Hidden/Post FX/Builtin Debug Views");
 		material.shaderKeywords = null;
 		if (context.isGBufferAvailable)
@@ -165,7 +165,7 @@
 	private void DepthPass(CommandBuffer cb)
 	{
 		Material mat = context.materialFactory.Get("Hidden/Post FX/Builtin Debug Views");
-		BuiltinDebugViewsModel.DepthSettings depth = base.model.settings.depth;
+		BuiltinDebugViewsModel.DepthSettings depth = model.settings.depth;
 		cb.SetGlobalFloat(Uniforms._DepthScale, 1f / depth.scale);
 		cb.Blit(null, BuiltinRenderTextureType.CameraTarget, mat, 0);
 	}
@@ -179,7 +179,7 @@
 	private void MotionVectorsPass(CommandBuffer cb)
 	{
 		Material material = context.materialFactory.Get("Hidden/Post FX/Builtin Debug Views");
-		BuiltinDebugViewsModel.MotionVectorsSettings motionVectors = base.model.settings.motionVectors;
+		BuiltinDebugViewsModel.MotionVectorsSettings motionVectors = model.settings.motionVectors;
 		int num = Uniforms._TempRT;
 		cb.GetTemporaryRT(num, context.width, context.height, 0, FilterMode.Bilinear);
 		cb.SetGlobalFloat(Uniforms._Opacity, motionVectors.sourceOpacity);
@@ -213,7 +213,7 @@
 
 	private void PrepareArrows()
 	{
-		int motionVectorsResolution = base.model.settings.motionVectors.motionVectorsResolution;
+		int motionVectorsResolution = model.settings.motionVectors.motionVectorsResolution;
 		int num = motionVectorsResolution * Screen.width / Screen.height;
 		if (m_Arrows == null)
 		{
```
