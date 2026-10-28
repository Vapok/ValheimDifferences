# `ArmorStand.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateAttach() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ArmorStand.cs
+++ b/ArmorStand.cs
@@ -329,6 +329,7 @@
 				itemData.m_stack = 1;
 				m_nview.GetZDO().Set(s_itemKeyHashes[m_queuedSlot], m_queuedItem.m_dropPrefab.name.GetStableHashCode());
 				m_nview.GetZDO().Set(s_variantKeyHashes[m_queuedSlot], itemData.m_variant);
+				itemData.m_equipped = false;
 				ItemDrop.SaveToZDO(itemData, m_nview.GetZDO(), m_queuedSlot);
 				localPlayer.UnequipItem(m_queuedItem);
 				localPlayer.GetInventory().RemoveOneItem(m_queuedItem);
```
