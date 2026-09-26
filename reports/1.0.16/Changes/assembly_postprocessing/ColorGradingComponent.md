# `UnityEngine.PostProcessing/ColorGradingComponent.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_postprocessing.dll`
* **Status**: `🟡 MODIFIED` (`+16/-16` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UnityEngine.PostProcessing/ColorGradingComponent.cs
+++ b/UnityEngine.PostProcessing/ColorGradingComponent.cs
@@ -59,7 +59,7 @@
 	{
 		get
 		{
-			if (base.model.enabled)
+			if (model.enabled)
 			{
 				return !context.interrupted;
 			}
@@ -222,7 +222,7 @@
 				filterMode = FilterMode.Bilinear
 			};
 		}
-		ColorGradingModel.CurvesSettings curves = base.model.settings.curves;
+		ColorGradingModel.CurvesSettings curves = model.settings.curves;
 		curves.hueVShue.Cache();
 		curves.hueVSsat.Cache();
 		for (int i = 0; i < 128; i++)
@@ -264,11 +264,11 @@
 
 	private void GenerateLut()
 	{
-		ColorGradingModel.Settings settings = base.model.settings;
-		if (!IsLogLutValid(base.model.bakedLut))
-		{
-			GraphicsUtils.Destroy(base.model.bakedLut);
-			base.model.bakedLut = new RenderTexture(1024, 32, 0, GetLutFormat())
+		ColorGradingModel.Settings settings = model.settings;
+		if (!IsLogLutValid(model.bakedLut))
+		{
+			GraphicsUtils.Destroy(model.bakedLut);
+			model.bakedLut = new RenderTexture(1024, 32, 0, GetLutFormat())
 			{
 				name = "Color Grading Log LUT",
 				hideFlags = HideFlags.DontSave,
@@ -278,7 +278,7 @@
 			};
 		}
 		Material material = context.materialFactory.Get("Hidden/Post FX/Lut Generator");
-		material.SetVector(Uniforms._LutParams, new Vector4(32f, 0.00048828125f, 1f / 64f, 1.032258f));
+		material.SetVector(Uniforms._LutParams, new Vector4(32f, 2f / 4096f, 1f / 64f, 1.032258f));
 		material.shaderKeywords = null;
 		ColorGradingModel.TonemappingSettings tonemapping = settings.tonemapping;
 		switch (tonemapping.tonemapper)
@@ -319,35 +319,35 @@
 		material.SetVector(Uniforms._ChannelMixerGreen, settings.channelMixer.green);
 		material.SetVector(Uniforms._ChannelMixerBlue, settings.channelMixer.blue);
 		material.SetTexture(Uniforms._Curves, GetCurveTexture());
-		Graphics.Blit(null, base.model.bakedLut, material, 0);
+		Graphics.Blit(null, model.bakedLut, material, 0);
 	}
 
 	public override void Prepare(Material uberMaterial)
 	{
-		if (base.model.isDirty || !IsLogLutValid(base.model.bakedLut))
+		if (model.isDirty || !IsLogLutValid(model.bakedLut))
 		{
 			GenerateLut();
-			base.model.isDirty = false;
+			model.isDirty = false;
 		}
 		uberMaterial.EnableKeyword(context.profile.debugViews.IsModeActive(BuiltinDebugViewsModel.Mode.PreGradingLog) ? "COLOR_GRADING_LOG_VIEW" : "COLOR_GRADING");
-		RenderTexture bakedLut = base.model.bakedLut;
+		RenderTexture bakedLut = model.bakedLut;
 		uberMaterial.SetTexture(Uniforms._LogLut, bakedLut);
 		uberMaterial.SetVector(Uniforms._LogLut_Params, new Vector3(1f / (float)bakedLut.width, 1f / (float)bakedLut.height, (float)bakedLut.height - 1f));
-		float value = Mathf.Exp(base.model.settings.basic.postExposure * 0.6931472f);
+		float value = Mathf.Exp(model.settings.basic.postExposure * 0.6931472f);
 		uberMaterial.SetFloat(Uniforms._ExposureEV, value);
 	}
 
 	public void OnGUI()
 	{
-		RenderTexture bakedLut = base.model.bakedLut;
+		RenderTexture bakedLut = model.bakedLut;
 		GUI.DrawTexture(new Rect(context.viewport.x * (float)Screen.width + 8f, 8f, bakedLut.width, bakedLut.height), bakedLut);
 	}
 
 	public override void OnDisable()
 	{
 		GraphicsUtils.Destroy(m_GradingCurves);
-		GraphicsUtils.Destroy(base.model.bakedLut);
+		GraphicsUtils.Destroy(model.bakedLut);
 		m_GradingCurves = null;
-		base.model.bakedLut = null;
+		model.bakedLut = null;
 	}
 }
```
