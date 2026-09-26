# `UnityEngine.PostProcessing/UserLutComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/UserLutComponent.cs
+++ b/UnityEngine.PostProcessing/UserLutComponent.cs
@@ -13,8 +13,8 @@
 	{
 		get
 		{
-			UserLutModel.Settings settings = base.model.settings;
-			if (base.model.enabled && settings.lut != null && settings.contribution > 0f && settings.lut.height == (int)Mathf.Sqrt(settings.lut.width))
+			UserLutModel.Settings settings = model.settings;
+			if (model.enabled && settings.lut != null && settings.contribution > 0f && settings.lut.height == (int)Mathf.Sqrt(settings.lut.width))
 			{
 				return !context.interrupted;
 			}
@@ -24,7 +24,7 @@
 
 	public override void Prepare(Material uberMaterial)
 	{
-		UserLutModel.Settings settings = base.model.settings;
+		UserLutModel.Settings settings = model.settings;
 		uberMaterial.EnableKeyword("USER_LUT");
 		uberMaterial.SetTexture(Uniforms._UserLut, settings.lut);
 		uberMaterial.SetVector(Uniforms._UserLut_Params, new Vector4(1f / (float)settings.lut.width, 1f / (float)settings.lut.height, (float)settings.lut.height - 1f, settings.contribution));
@@ -32,7 +32,7 @@
 
 	public void OnGUI()
 	{
-		UserLutModel.Settings settings = base.model.settings;
+		UserLutModel.Settings settings = model.settings;
 		GUI.DrawTexture(new Rect(context.viewport.x * (float)Screen.width + 8f, 8f, settings.lut.width, settings.lut.height), settings.lut);
 	}
 }
```
