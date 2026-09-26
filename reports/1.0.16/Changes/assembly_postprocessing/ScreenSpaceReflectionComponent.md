# `UnityEngine.PostProcessing/ScreenSpaceReflectionComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/ScreenSpaceReflectionComponent.cs
+++ b/UnityEngine.PostProcessing/ScreenSpaceReflectionComponent.cs
@@ -105,7 +105,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && context.isGBufferAvailable)
+			if (model.enabled && context.isGBufferAvailable)
 			{
 				return !context.interrupted;
 			}
@@ -139,7 +139,7 @@
 
 	public override void PopulateCommandBuffer(CommandBuffer cb)
 	{
-		ScreenSpaceReflectionModel.Settings settings = base.model.settings;
+		ScreenSpaceReflectionModel.Settings settings = model.settings;
 		Camera camera = context.camera;
 		int num = ((settings.reflection.reflectionQuality == ScreenSpaceReflectionModel.SSRResolution.High) ? 1 : 2);
 		int num2 = context.width / num;
@@ -177,7 +177,7 @@
 		material.SetVector(Uniforms._InvScreenSize, new Vector2(1f / num4, 1f / num5));
 		material.SetVector(Uniforms._ProjInfo, value2);
 		material.SetVector(Uniforms._CameraClipInfo, vector);
-		Matrix4x4 matrix4x = default(Matrix4x4);
+		Matrix4x4 matrix4x = default;
 		matrix4x.SetRow(0, new Vector4(num6, 0f, 0f, num6));
 		matrix4x.SetRow(1, new Vector4(0f, num7, 0f, num7));
 		matrix4x.SetRow(2, new Vector4(0f, 0f, 1f, 0f));
```
