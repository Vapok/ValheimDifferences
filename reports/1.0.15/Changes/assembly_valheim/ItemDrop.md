# `ItemDrop.cs` Diff (`1.0.14` $\rightarrow$ `1.0.15`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ItemDrop.cs
+++ b/ItemDrop.cs
@@ -866,7 +866,7 @@
 			{
 				m_stringBuilder.Append("\n<color=orange>" + item.m_shared.m_subtitle + "</color>");
 			}
-			if (item.m_cheated)
+			if (item.m_cheated && !PlayerProfile.s_bypassCheatChecks)
 			{
 				m_stringBuilder.Append("\n<color=#808080><i>" + Localization.instance.Localize("$achievements_cheated_item_inventory") + "</i></color>");
 			}
```
