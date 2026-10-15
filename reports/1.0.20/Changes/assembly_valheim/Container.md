# `Container.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `AddDefaultItems() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Container.cs
+++ b/Container.cs
@@ -103,7 +103,7 @@
 	{
 		foreach (ItemDrop.ItemData dropListItem in m_defaultItems.GetDropListItems())
 		{
-			if (m_nview.GetZDO().GetBool(ZDOVars.s_cheated) && !PlayerProfile.s_bypassCheatChecks)
+			if (m_nview.GetZDO().IsCheated() && !PlayerProfile.s_bypassCheatChecks)
 			{
 				dropListItem.m_cheated = true;
 			}
```
