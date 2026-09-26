# `GraphicsSettingsState.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GraphicsSettingsState.cs
+++ b/GraphicsSettingsState.cs
@@ -48,7 +48,7 @@
 
 	public static bool TryCreateFromPreset(GraphicsSettingsPreset preset, out GraphicsSettingsState state)
 	{
-		state = default(GraphicsSettingsState);
+		state = default;
 		int num = (int)(1u & (preset.TryGetQualitySetting(GraphicsSettingInt.FpsLimit, out state.m_presentSettings.m_fpsLimit) ? 1u : 0u) & (preset.TryGetQualitySetting(GraphicsSettingBool.Vsync, out state.m_presentSettings.m_vsync) ? 1u : 0u)) & (preset.TryGetQualitySetting(GraphicsSettingInt.Vegetation, out int value) ? 1 : 0);
 		state.m_vegetation = (ClutterSystem.Quality)value;
 		int num2 = (int)((uint)num & (preset.TryGetQualitySetting(GraphicsSettingInt.LOD, out state.m_lod) ? 1u : 0u) & (preset.TryGetQualitySetting(GraphicsSettingInt.Lights, out state.m_lights) ? 1u : 0u) & (preset.TryGetQualitySetting(GraphicsSettingInt.ShadowQuality, out state.m_shadowQuality) ? 1u : 0u) & (preset.TryGetQualitySetting(GraphicsSettingInt.PointLights, out state.m_pointLights) ? 1u : 0u) & (preset.TryGetQualitySetting(GraphicsSettingInt.PointLightShadows, out state.m_pointLightShadows) ? 1u : 0u) & (preset.TryGetQualitySetting(GraphicsSettingInt.SSAO, out state.m_ssao) ? 1u : 0u) & (preset.TryGetQualitySetting(GraphicsSettingInt.Target3DResolutionVertical, out state.m_target3DResolutionVertical) ? 1u : 0u)) & (preset.TryGetQualitySetting(GraphicsSettingInt.UpscalingAlgorithm, out int value2) ? 1 : 0);
```
