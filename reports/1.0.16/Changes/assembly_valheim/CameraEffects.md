# `CameraEffects.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CameraEffects.cs
+++ b/CameraEffects.cs
@@ -138,7 +138,7 @@
 		if (m_dof.enabled && m_dofAutoFocus)
 		{
 			float num = m_dofMaxDistance;
-			if (Physics.Raycast(base.transform.position, base.transform.forward, out var hitInfo, m_dofMaxDistance, m_dofRayMask))
+			if (Physics.Raycast(transform.position, transform.forward, out var hitInfo, m_dofMaxDistance, m_dofRayMask))
 			{
 				num = hitInfo.distance;
 			}
```
