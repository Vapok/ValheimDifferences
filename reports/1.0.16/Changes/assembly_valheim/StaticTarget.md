# `StaticTarget.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/StaticTarget.cs
+++ b/StaticTarget.cs
@@ -38,10 +38,10 @@
 				}
 			}
 			m_localCenter /= (float)m_colliders.Count;
-			m_localCenter = base.transform.InverseTransformPoint(m_localCenter);
+			m_localCenter = transform.InverseTransformPoint(m_localCenter);
 			m_haveCenter = true;
 		}
-		return base.transform.TransformPoint(m_localCenter);
+		return transform.TransformPoint(m_localCenter);
 	}
 
 	public List<Collider> GetAllColliders()
@@ -68,7 +68,7 @@
 		List<Collider> allColliders = GetAllColliders();
 		if (allColliders.Count == 0)
 		{
-			return base.transform.position;
+			return transform.position;
 		}
 		float num = 9999999f;
 		Vector3 result = Vector3.zero;
```
