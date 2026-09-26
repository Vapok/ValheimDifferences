# `SiegeMachine.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SiegeMachine.cs
+++ b/SiegeMachine.cs
@@ -80,7 +80,7 @@
 		m_nview = GetComponent<ZNetView>();
 		if (m_nview.GetZDO() == null)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 	}
 
```
