# `InventoryGui.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `DoCrafting() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/InventoryGui.cs
+++ b/InventoryGui.cs
@@ -1885,7 +1885,12 @@
 					{
 						if (requirement2.m_recover)
 						{
-							int num5 = Mathf.CeilToInt((float)(requirement2.GetAmount(1) + requirement2.GetAmount(num - 1)) * itemData2.m_shared.m_breakReturnIngreientsAmount);
+							int num5 = 0;
+							for (int k = 1; k < num; k++)
+							{
+								num5 += requirement2.GetAmount(k);
+							}
+							num5 = Mathf.RoundToInt((float)num5 * itemData2.m_shared.m_breakReturnIngreientsAmount);
 							if (num5 > 0)
 							{
 								itemData = player.GetInventory().AddItem(requirement2.m_resItem.name, num5, requirement2.m_resItem.m_itemData.m_quality, requirement2.m_resItem.m_itemData.m_variant, playerID, playerName, new Vector2i(-1, -1), cheated);
```
