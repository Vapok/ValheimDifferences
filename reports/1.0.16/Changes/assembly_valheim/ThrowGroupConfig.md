# `Valheim.UI/ThrowGroupConfig.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/ThrowGroupConfig.cs
+++ b/Valheim.UI/ThrowGroupConfig.cs
@@ -30,7 +30,15 @@
 			return;
 		}
 		RadialMenuElement selected = radial.Selected;
-		ItemDrop.ItemData itemData = ((selected is ItemElement itemElement) ? itemElement.m_data : ((!(selected is ThrowElement throwElement)) ? m_storedItemData : throwElement.m_data));
+		ItemDrop.ItemData itemData;
+		if (selected is ItemElement itemElement)
+		{
+			itemData = itemElement.m_data;
+		}
+		else
+		{
+			itemData = ((!(selected is ThrowElement throwElement)) ? m_storedItemData : throwElement.m_data);
+		}
 		ItemDrop.ItemData itemData2 = itemData;
 		if (itemData2 == null)
 		{
```
