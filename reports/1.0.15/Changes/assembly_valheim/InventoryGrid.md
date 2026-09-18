# `InventoryGrid.cs` Diff (`1.0.14` $\rightarrow$ `1.0.15`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InventoryGrid.cs
+++ b/InventoryGrid.cs
@@ -576,7 +576,7 @@
 		{
 			return true;
 		}
-		if (itemAt != null && (itemAt.m_shared.m_name != item.m_shared.m_name || (item.m_shared.m_maxQuality > 1 && itemAt.m_quality != item.m_quality) || itemAt.m_shared.m_maxStackSize == 1 || itemAt.m_cheated != item.m_cheated) && item.m_stack == amount)
+		if (itemAt != null && (itemAt.m_shared.m_name != item.m_shared.m_name || (item.m_shared.m_maxQuality > 1 && itemAt.m_quality != item.m_quality) || itemAt.m_shared.m_maxStackSize == 1) && item.m_stack == amount)
 		{
 			fromInventory.RemoveItem(item);
 			fromInventory.MoveItemToThis(m_inventory, itemAt, itemAt.m_stack, item.m_gridPos.x, item.m_gridPos.y);
```
