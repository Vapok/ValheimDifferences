# `InputDefinition.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InputDefinition.cs
+++ b/InputDefinition.cs
@@ -117,7 +117,7 @@
 		}
 		m_keyCode = button;
 		m_axisName = null;
-		m_axisRange = default(FloatRange);
+		m_axisRange = default;
 		m_outputRange = new FloatRange(0f, 1f);
 		m_advancedMap = null;
 		m_parentGamepad = gamepad;
@@ -131,7 +131,7 @@
 		}
 		m_keyCode = button;
 		m_axisName = null;
-		m_axisRange = default(FloatRange);
+		m_axisRange = default;
 		m_outputRange = outputRange;
 		m_advancedMap = null;
 		m_parentGamepad = gamepad;
```
