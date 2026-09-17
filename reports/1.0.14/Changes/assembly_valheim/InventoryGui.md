# `InventoryGui.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InventoryGui.cs
+++ b/InventoryGui.cs
@@ -479,9 +479,9 @@
 
 	private bool CanDropDragOntoItem(ItemDrop.ItemData item)
 	{
-		if (item.IsSameType(m_dragItem))
-		{
-			return item.GetSpaceLeftInStack() > 0;
+		if (item.IsSameType(m_dragItem) && item.GetSpaceLeftInStack() > 0)
+		{
+			return item.m_cheated == m_dragItem.m_cheated;
 		}
 		return false;
 	}
```
