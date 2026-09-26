# `NavmeshTest.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/NavmeshTest.cs
+++ b/NavmeshTest.cs
@@ -19,7 +19,7 @@
 
 	private void Update()
 	{
-		if (Pathfinding.instance.GetPath(base.transform.position, m_target.position, m_path, m_agentType, requireFullPath: false, m_cleanPath))
+		if (Pathfinding.instance.GetPath(transform.position, m_target.position, m_path, m_agentType, requireFullPath: false, m_cleanPath))
 		{
 			m_havePath = true;
 		}
@@ -48,14 +48,14 @@
 				Gizmos.DrawSphere(item + Vector3.up * 0.2f, 0.1f);
 			}
 			Gizmos.color = Color.green;
-			Gizmos.DrawSphere(base.transform.position, 0.3f);
+			Gizmos.DrawSphere(transform.position, 0.3f);
 			Gizmos.DrawSphere(m_target.position, 0.3f);
 		}
 		else
 		{
 			Gizmos.color = Color.red;
-			Gizmos.DrawLine(base.transform.position + Vector3.up * 0.2f, m_target.position + Vector3.up * 0.2f);
-			Gizmos.DrawSphere(base.transform.position, 0.3f);
+			Gizmos.DrawLine(transform.position + Vector3.up * 0.2f, m_target.position + Vector3.up * 0.2f);
+			Gizmos.DrawSphere(transform.position, 0.3f);
 			Gizmos.DrawSphere(m_target.position, 0.3f);
 		}
 	}
```
