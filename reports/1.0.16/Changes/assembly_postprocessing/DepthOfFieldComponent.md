# `UnityEngine.PostProcessing/DepthOfFieldComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/DepthOfFieldComponent.cs
+++ b/UnityEngine.PostProcessing/DepthOfFieldComponent.cs
@@ -39,7 +39,7 @@
 	{
 		get
 		{
-			if (base.model.enabled)
+			if (model.enabled)
 			{
 				return !context.interrupted;
 			}
@@ -54,7 +54,7 @@
 
 	private float CalculateFocalLength()
 	{
-		DepthOfFieldModel.Settings settings = base.model.settings;
+		DepthOfFieldModel.Settings settings = model.settings;
 		if (!settings.useCameraFov)
 		{
 			return settings.focalLength / 1000f;
@@ -65,7 +65,7 @@
 
 	private float CalculateMaxCoCRadius(int screenHeight)
 	{
-		float num = (float)base.model.settings.kernelSize * 4f + 6f;
+		float num = (float)model.settings.kernelSize * 4f + 6f;
 		return Mathf.Min(0.05f, num / (float)screenHeight);
 	}
 
@@ -93,7 +93,7 @@
 
 	public void Prepare(RenderTexture source, Material uberMaterial, bool antialiasCoC, Vector2 taaJitter, float taaBlending)
 	{
-		DepthOfFieldModel.Settings settings = base.model.settings;
+		DepthOfFieldModel.Settings settings = model.settings;
 		RenderTextureFormat format = RenderTextureFormat.DefaultHDR;
 		RenderTextureFormat format2 = SelectFormat(RenderTextureFormat.R8, RenderTextureFormat.RHalf);
 		float num = CalculateFocalLength();
```
