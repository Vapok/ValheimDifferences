# `EnvMan.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+20/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetDayFraction() [Method Body Modified]`
- `SetEnv() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/EnvMan.cs
+++ b/EnvMan.cs
@@ -91,6 +91,11 @@
 	public float _SnowGlintViewAmount = 0.5f;
 
 	public float _SnowGlintTimeAmount = 3f;
+
+	[Header("Accessibility")]
+	public float m_accessibilityMinimumBrightnessHeadroom = 0.25f;
+
+	public float m_accessibilityBrightnessMultiplier = 4f;
 
 	[Header("Other")]
 	public MeshRenderer m_clouds;
@@ -874,7 +879,15 @@
 		RenderSettings.fogDensity += env.m_fogDensityMorning * morningInt;
 		RenderSettings.fogDensity += env.m_fogDensityEvening * eveningInt;
 		RenderSettings.ambientMode = AmbientMode.Flat;
-		RenderSettings.ambientLight = Color.Lerp(env.m_ambColorNight, env.m_ambColorDay, dayInt);
+		Color color = env.m_ambColorDay;
+		Color color2 = env.m_ambColorNight;
+		float num = PlayerPrefs.GetFloat("AccessibilityBrightness", 0f);
+		if (num > 0f)
+		{
+			color = ColorUtils.ApplyBrightnessMultiplier(color, m_accessibilityBrightnessMultiplier, m_accessibilityMinimumBrightnessHeadroom, num);
+			color2 = ColorUtils.ApplyBrightnessMultiplier(color2, m_accessibilityBrightnessMultiplier, color, m_accessibilityMinimumBrightnessHeadroom, num);
+		}
+		RenderSettings.ambientLight = Color.Lerp(color2, color, dayInt);
 		SunShafts component = mainCamera.GetComponent<SunShafts>();
 		if ((bool)component)
 		{
@@ -926,12 +939,12 @@
 		float globalFloat = Shader.GetGlobalFloat(s_wet);
 		globalFloat = Mathf.MoveTowards(globalFloat, env.m_isWet ? 1f : 0f, dt / m_wetTransitionDuration);
 		Shader.SetGlobalFloat(s_wet, globalFloat);
-		float num = 0f;
-		num += env.m_auroraIntensityDay * dayInt;
-		num += env.m_auroraIntensityEvening * eveningInt;
-		num += env.m_auroraIntensityMorning * morningInt;
-		num += env.m_auroraIntensityNight * nightInt;
-		Shader.SetGlobalFloat(s_auroraIntensity, num);
+		float num2 = 0f;
+		num2 += env.m_auroraIntensityDay * dayInt;
+		num2 += env.m_auroraIntensityEvening * eveningInt;
+		num2 += env.m_auroraIntensityMorning * morningInt;
+		num2 += env.m_auroraIntensityNight * nightInt;
+		Shader.SetGlobalFloat(s_auroraIntensity, num2);
 	}
 
 	public float GetDayFraction()
```
