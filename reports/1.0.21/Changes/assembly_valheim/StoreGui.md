# `StoreGui.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Show() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/StoreGui.cs
+++ b/StoreGui.cs
@@ -110,6 +110,7 @@
 		{
 			m_trader = trader;
 			m_rootPanel.SetActive(value: true);
+			ZInput.ResetButtonStatus("Use");
 			FillList();
 		}
 	}
```
