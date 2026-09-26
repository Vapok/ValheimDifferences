# `GraphicsSettingsPreset.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GraphicsSettingsPreset.cs
+++ b/GraphicsSettingsPreset.cs
@@ -28,7 +28,7 @@
 		{
 			return m_type.ToString();
 		}
-		return base.name;
+		return name;
 	}
 
 	public bool TryGetQualitySetting(GraphicsSettingInt setting, out int value)
@@ -60,7 +60,7 @@
 		}
 		catch (Exception arg)
 		{
-			ZLog.LogError($"Preset {base.name}: {arg}");
+			ZLog.LogError($"Preset {name}: {arg}");
 		}
 	}
 }
```
