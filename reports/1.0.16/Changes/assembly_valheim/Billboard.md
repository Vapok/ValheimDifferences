# `Billboard.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Billboard.cs
+++ b/Billboard.cs
@@ -10,7 +10,7 @@
 
 	private void Awake()
 	{
-		m_normal = base.transform.up;
+		m_normal = transform.up;
 	}
 
 	private void LateUpdate()
@@ -21,16 +21,16 @@
 			Vector3 vector = mainCamera.transform.position;
 			if (m_invert)
 			{
-				vector = base.transform.position - (vector - base.transform.position);
+				vector = transform.position - (vector - transform.position);
 			}
 			if (m_vertical)
 			{
-				vector.y = base.transform.position.y;
-				base.transform.LookAt(vector, m_normal);
+				vector.y = transform.position.y;
+				transform.LookAt(vector, m_normal);
 			}
 			else
 			{
-				base.transform.LookAt(vector);
+				transform.LookAt(vector);
 			}
 		}
 	}
```
