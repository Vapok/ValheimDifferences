# `UnityEngine.PostProcessing/VignetteComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/VignetteComponent.cs
+++ b/UnityEngine.PostProcessing/VignetteComponent.cs
@@ -19,7 +19,7 @@
 	{
 		get
 		{
-			if (base.model.enabled)
+			if (model.enabled)
 			{
 				return !context.interrupted;
 			}
@@ -29,7 +29,7 @@
 
 	public override void Prepare(Material uberMaterial)
 	{
-		VignetteModel.Settings settings = base.model.settings;
+		VignetteModel.Settings settings = model.settings;
 		uberMaterial.SetColor(Uniforms._Vignette_Color, settings.color);
 		if (settings.mode == VignetteModel.Mode.Classic)
 		{
```
