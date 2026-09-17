# `Valheim.SettingsGui/GamepadSettings.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/GamepadSettings.cs
+++ b/Valheim.SettingsGui/GamepadSettings.cs
@@ -154,9 +154,9 @@
 
 	private const string GlyphsPlaystation = "Playstation";
 
-	public static float m_motionSensorYAxisSensitivity = 1f;
-
-	public static float m_motionSensorXAxisSensitivity = 1f;
+	public static float m_motionSensorYAxisSensitivity;
+
+	public static float m_motionSensorXAxisSensitivity;
 
 	private List<string> m_glyphOptions = new List<string> { "Xbox", "Playstation" };
 
```
