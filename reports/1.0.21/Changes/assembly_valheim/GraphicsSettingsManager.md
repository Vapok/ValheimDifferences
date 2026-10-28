# `GraphicsSettingsManager.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `RequestTargetFrameRateFromPreset() [Method Body Modified]`
- `ScaleTarget3DResolutionByCurrentRenderingArea() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/GraphicsSettingsManager.cs
+++ b/GraphicsSettingsManager.cs
@@ -392,9 +392,9 @@
 	{
 		GraphicsSettingsState currentSettingsWithCurrentPresetApplied = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: true, forceSelected: true);
 		GraphicsSettingsState currentSettingsWithCurrentPresetApplied2 = GetCurrentSettingsWithCurrentPresetApplied(includeBackground: false, forceSelected: true);
+		m_presentManager.SetVSyncEnabled(currentSettingsWithCurrentPresetApplied.m_presentSettings.m_vsync);
 		int fpsLimit = currentSettingsWithCurrentPresetApplied.m_presentSettings.m_fpsLimit;
 		m_presentManager.RequestTargetFrameRate(fpsLimit, currentSettingsWithCurrentPresetApplied2.m_presentSettings.m_fpsLimit);
-		m_presentManager.SetVSyncEnabled(currentSettingsWithCurrentPresetApplied.m_presentSettings.m_vsync);
 	}
 
 	private static int ScaleTarget3DResolutionByCurrentRenderingArea(int target3DResolutionVertical)
```
