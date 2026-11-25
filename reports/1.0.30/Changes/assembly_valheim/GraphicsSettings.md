# `Valheim.SettingsGui/GraphicsSettings.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GetDisplayValue() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Valheim.SettingsGui/GraphicsSettings.cs
+++ b/Valheim.SettingsGui/GraphicsSettings.cs
@@ -1098,6 +1098,11 @@
 			return GetQualityText(Math.Max(0, value - 1));
 		case GraphicsSettingInt.LOD:
 		case GraphicsSettingInt.Lights:
+			if (value == -1)
+			{
+				return Localization.instance.Localize("[$hud_off]");
+			}
+			return GetQualityText(value);
 		case GraphicsSettingInt.ShadowQuality:
 			return GetQualityText(value);
 		case GraphicsSettingInt.SimulationDistance:
```
