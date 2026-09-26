# `ClutterSystem.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ClutterSystem.cs
+++ b/ClutterSystem.cs
@@ -133,7 +133,7 @@
 			ApplySettings();
 			m_placeRayMask = LayerMask.GetMask("terrain");
 			m_grassRoot = new GameObject("grassroot");
-			m_grassRoot.transform.SetParent(base.transform);
+			m_grassRoot.transform.SetParent(transform);
 		}
 	}
 
```
