# `InventoryElement.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InventoryElement.cs
+++ b/InventoryElement.cs
@@ -59,7 +59,7 @@
 		{
 			return m_touchRect;
 		}
-		return base.transform as RectTransform;
+		return transform as RectTransform;
 	}
 
 	public void UpdateHighlightColor()
```
