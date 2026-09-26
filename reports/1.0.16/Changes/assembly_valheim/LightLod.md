# `LightLod.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LightLod.cs
+++ b/LightLod.cs
@@ -80,7 +80,7 @@
 			if ((object)Utils.GetMainCamera() != null && (bool)m_light)
 			{
 				Vector3 lightReferencePoint = GetLightReferencePoint();
-				float distance = Vector3.Distance(lightReferencePoint, base.transform.position);
+				float distance = Vector3.Distance(lightReferencePoint, transform.position);
 				if (m_lightLod)
 				{
 					if (distance < m_lightDistance && (m_lightPrio < m_lightLimit || m_lightLimit < 0))
@@ -182,12 +182,12 @@
 		if (m_lightLod)
 		{
 			Gizmos.color = Color.yellow;
-			Gizmos.DrawWireSphere(base.transform.position, m_lightDistance);
+			Gizmos.DrawWireSphere(transform.position, m_lightDistance);
 		}
 		if (m_shadowLod)
 		{
 			Gizmos.color = Color.grey;
-			Gizmos.DrawWireSphere(base.transform.position, m_shadowDistance);
+			Gizmos.DrawWireSphere(transform.position, m_shadowDistance);
 		}
 	}
 }
```
