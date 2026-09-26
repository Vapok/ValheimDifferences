# `UnityEngine.PostProcessing/ChromaticAberrationComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/ChromaticAberrationComponent.cs
+++ b/UnityEngine.PostProcessing/ChromaticAberrationComponent.cs
@@ -15,7 +15,7 @@
 	{
 		get
 		{
-			if (base.model.enabled && base.model.settings.intensity > 0f)
+			if (model.enabled && model.settings.intensity > 0f)
 			{
 				return !context.interrupted;
 			}
@@ -31,7 +31,7 @@
 
 	public override void Prepare(Material uberMaterial)
 	{
-		ChromaticAberrationModel.Settings settings = base.model.settings;
+		ChromaticAberrationModel.Settings settings = model.settings;
 		Texture2D texture2D = settings.spectralTexture;
 		if (texture2D == null)
 		{
```
