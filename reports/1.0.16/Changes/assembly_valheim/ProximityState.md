# `ProximityState.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ProximityState.cs
+++ b/ProximityState.cs
@@ -34,7 +34,7 @@
 			if (!m_animator.GetBool("near"))
 			{
 				m_animator.SetBool("near", value: true);
-				m_movingClose.Create(base.transform.position, base.transform.rotation);
+				m_movingClose.Create(transform.position, transform.rotation);
 			}
 		}
 	}
@@ -45,7 +45,7 @@
 		if (m_near.Count == 0 && m_animator.GetBool("near"))
 		{
 			m_animator.SetBool("near", value: false);
-			m_movingAway.Create(base.transform.position, base.transform.rotation);
+			m_movingAway.Create(transform.position, transform.rotation);
 		}
 	}
 }
```
