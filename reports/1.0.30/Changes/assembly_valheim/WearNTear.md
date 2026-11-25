# `WearNTear.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateSupport() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/WearNTear.cs
+++ b/WearNTear.cs
@@ -850,7 +850,7 @@
 				}
 				num++;
 			}
-			if (num == m_supportPositions.Count && num2 >= m_support)
+			if (num == m_supportPositions.Count && num2 > m_support)
 			{
 				return;
 			}
```
