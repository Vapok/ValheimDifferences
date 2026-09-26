# `StaticRotation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StaticRotation.cs
+++ b/StaticRotation.cs
@@ -39,7 +39,7 @@
 		m_rotation = zDO.GetFloat(ZDOVars.s_tiltrot);
 		if (m_rotation == 0f)
 		{
-			m_rotation = base.transform.rotation.eulerAngles.y;
+			m_rotation = transform.rotation.eulerAngles.y;
 			if (zDO.IsOwner())
 			{
 				zDO.Set(ZDOVars.s_tiltrot, m_rotation);
@@ -51,8 +51,8 @@
 	{
 		if (!m_disabled)
 		{
-			Vector3 eulerAngles = base.transform.rotation.eulerAngles;
-			base.transform.rotation = Quaternion.Euler(eulerAngles.x, m_rotation, eulerAngles.z);
+			Vector3 eulerAngles = transform.rotation.eulerAngles;
+			transform.rotation = Quaternion.Euler(eulerAngles.x, m_rotation, eulerAngles.z);
 		}
 	}
 }
```
