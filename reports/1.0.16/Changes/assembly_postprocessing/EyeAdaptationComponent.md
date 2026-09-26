# `UnityEngine.PostProcessing/EyeAdaptationComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/EyeAdaptationComponent.cs
+++ b/UnityEngine.PostProcessing/EyeAdaptationComponent.cs
@@ -43,7 +43,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && SystemInfo.supportsComputeShaders)
+			if (model.enabled && SystemInfo.supportsComputeShaders)
 			{
 				return !context.interrupted;
 			}
@@ -82,7 +82,7 @@
 
 	private Vector4 GetHistogramScaleOffsetRes()
 	{
-		EyeAdaptationModel.Settings settings = base.model.settings;
+		EyeAdaptationModel.Settings settings = model.settings;
 		float num = settings.logMax - settings.logMin;
 		float num2 = 1f / num;
 		float y = (float)(-settings.logMin) * num2;
@@ -91,7 +91,7 @@
 
 	public Texture Prepare(RenderTexture source, Material uberMaterial)
 	{
-		EyeAdaptationModel.Settings settings = base.model.settings;
+		EyeAdaptationModel.Settings settings = model.settings;
 		if (m_EyeCompute == null)
 		{
 			m_EyeCompute = Resources.Load<ComputeShader>("Shaders/EyeHistogram");
```
