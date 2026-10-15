# `Piece.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Piece.cs
+++ b/Piece.cs
@@ -378,7 +378,7 @@
 					{
 						container = UnityEngine.Object.Instantiate(m_destroyedLootPrefab, transform.position + Vector3.up * m_returnResourceHeightOffset, Quaternion.identity).GetComponent<Container>();
 					}
-					if (m_nview.GetZDO().GetBool(ZDOVars.s_cheated) && !PlayerProfile.s_bypassCheatChecks)
+					if (m_nview.GetZDO().IsCheated() && !PlayerProfile.s_bypassCheatChecks)
 					{
 						itemData.m_cheated = true;
 					}
@@ -391,7 +391,7 @@
 				ItemDrop component2 = UnityEngine.Object.Instantiate(itemPrefab, transform.position + Vector3.up * m_returnResourceHeightOffset, Quaternion.identity).GetComponent<ItemDrop>();
 				component2.SetStack(Mathf.Min(dropCount, component2.m_itemData.m_shared.m_maxStackSize));
 				ItemDrop.OnCreateNew(component2);
-				if (m_nview.GetZDO().GetBool(ZDOVars.s_cheated) && !PlayerProfile.s_bypassCheatChecks)
+				if (m_nview.GetZDO().IsCheated() && !PlayerProfile.s_bypassCheatChecks)
 				{
 					component2.m_itemData.m_cheated = true;
 				}
```
