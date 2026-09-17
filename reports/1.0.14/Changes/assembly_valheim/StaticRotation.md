# `StaticRotation.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StaticRotation.cs
+++ b/StaticRotation.cs
@@ -32,12 +32,16 @@
 			return;
 		}
 		ZDO zDO = m_nview.GetZDO();
-		if (zDO != null && zDO.IsValid())
+		if (zDO == null || !zDO.IsValid())
 		{
-			m_rotation = zDO.GetFloat(ZDOVars.s_tiltrot);
-			if (m_rotation == 0f)
+			return;
+		}
+		m_rotation = zDO.GetFloat(ZDOVars.s_tiltrot);
+		if (m_rotation == 0f)
+		{
+			m_rotation = base.transform.rotation.eulerAngles.y;
+			if (zDO.IsOwner())
 			{
-				m_rotation = base.transform.rotation.eulerAngles.y;
 				zDO.Set(ZDOVars.s_tiltrot, m_rotation);
 			}
 		}
```
