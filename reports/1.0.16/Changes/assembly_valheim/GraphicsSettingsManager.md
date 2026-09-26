# `GraphicsSettingsManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+22/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GraphicsSettingsManager.cs
+++ b/GraphicsSettingsManager.cs
@@ -196,10 +196,10 @@
 	{
 		if (s_instance != null)
 		{
-			UnityEngine.Object.Destroy(base.gameObject);
+			UnityEngine.Object.Destroy(gameObject);
 			return;
 		}
-		UnityEngine.Object.DontDestroyOnLoad(base.gameObject);
+		UnityEngine.Object.DontDestroyOnLoad(gameObject);
 		s_instance = this;
 		m_presentManager.Initialize();
 		m_presentManager.RequestTargetFrameRate(60, 60);
@@ -283,7 +283,10 @@
 
 	private void Initialize()
 	{
-		QualitySettings.maxQueuedFrames = 2;
+		if (!Application.isConsolePlatform)
+		{
+			QualitySettings.maxQueuedFrames = 2;
+		}
 		m_isInitialized = true;
 		if (LoadGraphicsConfigurationForCurrentPlatform())
 		{
@@ -451,7 +454,14 @@
 		if (num < 0)
 		{
 			bool flag = PlatformPrefs.GetBool("SSAO");
-			num = ((flag != PlatformPrefs.GetBool("SSAO", defaultValue: true)) ? s_defaultGraphicsSettings.m_ssao : (flag ? GraphicsSettingInt.SSAO.GetRange().m_maxValue : GraphicsSettingInt.SSAO.GetRange().m_minValue));
+			if (flag != PlatformPrefs.GetBool("SSAO", defaultValue: true))
+			{
+				num = s_defaultGraphicsSettings.m_ssao;
+			}
+			else
+			{
+				num = (flag ? GraphicsSettingInt.SSAO.GetRange().m_maxValue : GraphicsSettingInt.SSAO.GetRange().m_minValue);
+			}
 		}
 		m_currentPlayerSettings = new GraphicsSettingsState
 		{
@@ -489,7 +499,14 @@
 		if (num < 0)
 		{
 			float num2 = PlatformPrefs.GetFloat("RenderScale", float.NaN);
-			num = (float.IsNaN(num2) ? s_defaultGraphicsSettings.m_target3DResolutionVertical : ((num2 != 1f) ? Mathf.RoundToInt((float)Screen.height * num2) : int.MaxValue));
+			if (float.IsNaN(num2))
+			{
+				num = s_defaultGraphicsSettings.m_target3DResolutionVertical;
+			}
+			else
+			{
+				num = ((num2 != 1f) ? Mathf.RoundToInt((float)Screen.height * num2) : int.MaxValue);
+			}
 		}
 		return num;
 	}
```
