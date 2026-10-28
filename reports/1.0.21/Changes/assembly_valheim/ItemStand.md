# `ItemStand.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateAttach() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ItemStand.cs
+++ b/ItemStand.cs
@@ -373,6 +373,7 @@
 				itemData.m_stack = 1;
 				int stableHashCode = m_queuedItem.m_dropPrefab.name.GetStableHashCode();
 				m_nview.GetZDO().Set(ZDOVars.s_item, stableHashCode);
+				itemData.m_equipped = false;
 				ItemDrop.SaveToZDO(itemData, m_nview.GetZDO());
 				localPlayer.UnequipItem(m_queuedItem);
 				localPlayer.GetInventory().RemoveOneItem(m_queuedItem);
```
