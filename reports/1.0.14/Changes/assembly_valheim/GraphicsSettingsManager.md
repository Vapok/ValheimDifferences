# `GraphicsSettingsManager.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private static void ApplyShaderKeywords(in GraphicsSettingsState settings)`
- `private void ApplyTesselation(in GraphicsSettingsState settings)`

---

## 📝 Code Diff

```diff
--- a/GraphicsSettingsManager.cs
+++ b/GraphicsSettingsManager.cs
@@ -56,6 +56,9 @@
 	[SerializeField]
 	private GlobalGraphicsConfiguration m_globalConfig;
 
+	[SerializeField]
+	private Shader[] m_tesselationShaders = new Shader[0];
+
 	private PresentManager m_presentManager = new PresentManager();
 
 	private SoftReference<GraphicsConfiguration> m_config;
@@ -199,7 +202,7 @@
 		UnityEngine.Object.DontDestroyOnLoad(base.gameObject);
 		s_instance = this;
 		m_presentManager.Initialize();
-		m_presentManager.RequestTargetFrameRate(60);
+		m_presentManager.RequestTargetFrameRate(60, 60);
 		m_presentManager.TargetFrameRateChanged += ApplyGraphicsSettingsToCurrentSession;
 		m_presentManager.ResolutionChanged += ApplyGraphicsSettingsToCurrentSession;
 		if (PlatformManager.DistributionPlatform != null)
@@ -375,7 +378,7 @@
 			RequestTargetFrameRateFromPreset();
 			m_activeSettings = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: true, out var _);
 			ApplyTargetResolutionSetting(ScaleTarget3DResolutionByCurrentRenderingArea(m_activeSettings.m_target3DResolutionVertical), m_activeSettings.m_upscalingAlgorithm);
-			ApplyShaderKeywords(in m_activeSettings);
+			ApplyTesselation(in m_activeSettings);
 			ApplyQualitySettings(in m_activeSettings);
 			ApplyLightLod(in m_activeSettings);
 			GraphicsSettingsChanged?.Invoke();
@@ -385,8 +388,9 @@
 	private void RequestTargetFrameRateFromPreset()
 	{
 		GraphicsSettingsState currentSettingsWithCurrentPresetApplied = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: true, forceSelected: true);
+		GraphicsSettingsState currentSettingsWithCurrentPresetApplied2 = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: false, forceSelected: true);
 		int fpsLimit = currentSettingsWithCurrentPresetApplied.m_presentSettings.m_fpsLimit;
-		m_presentManager.RequestTargetFrameRate(fpsLimit);
+		m_presentManager.RequestTargetFrameRate(fpsLimit, currentSettingsWithCurrentPresetApplied2.m_presentSettings.m_fpsLimit);
 		m_presentManager.SetVSyncEnabled(currentSettingsWithCurrentPresetApplied.m_presentSettings.m_vsync);
 	}
 
@@ -661,7 +665,7 @@
 		LightLod.m_shadowLimit = GetPointLightShadowLimit(settings.m_pointLightShadows);
 	}
 
-	private static void ApplyShaderKeywords(in GraphicsSettingsState settings)
+	private void ApplyTesselation(in GraphicsSettingsState settings)
 	{
 		if (settings.m_tesselation)
 		{
@@ -671,5 +675,9 @@
 		{
 			Shader.DisableKeyword("TESSELATION_ON");
 		}
+		for (int i = 0; i < m_tesselationShaders.Length; i++)
+		{
+			m_tesselationShaders[i].maximumLOD = (settings.m_tesselation ? 250 : 200);
+		}
 	}
 }
```
