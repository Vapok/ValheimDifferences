# `UnityEngine.PostProcessing/FxaaComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/FxaaComponent.cs
+++ b/UnityEngine.PostProcessing/FxaaComponent.cs
@@ -13,7 +13,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && base.model.settings.method == AntialiasingModel.Method.Fxaa)
+			if (model.enabled && model.settings.method == AntialiasingModel.Method.Fxaa)
 			{
 				return !context.interrupted;
 			}
@@ -23,7 +23,7 @@
 
 	public void Render(RenderTexture source, RenderTexture destination)
 	{
-		AntialiasingModel.FxaaSettings fxaaSettings = base.model.settings.fxaaSettings;
+		AntialiasingModel.FxaaSettings fxaaSettings = model.settings.fxaaSettings;
 		Material material = context.materialFactory.Get("Hidden/Post FX/FXAA");
 		AntialiasingModel.FxaaQualitySettings fxaaQualitySettings = AntialiasingModel.FxaaQualitySettings.presets[(int)fxaaSettings.preset];
 		AntialiasingModel.FxaaConsoleSettings fxaaConsoleSettings = AntialiasingModel.FxaaConsoleSettings.presets[(int)fxaaSettings.preset];
```
