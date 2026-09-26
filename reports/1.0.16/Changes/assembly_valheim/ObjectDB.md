# `ObjectDB.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `public List<ItemDrop> GetAllFoodItems()`
- `public List<ItemDrop> GetAllFoodItems(List<GameObject> itemsExcluded)`

---

## 📝 Code Diff

```diff
--- a/ObjectDB.cs
+++ b/ObjectDB.cs
@@ -213,7 +213,7 @@
 		return m_creatableFood;
 	}
 
-	public List<ItemDrop> GetAllFoodItems()
+	public List<ItemDrop> GetAllFoodItems(List<GameObject> itemsExcluded)
 	{
 		if (m_foodItems != null && m_foodItems.Count > 0)
 		{
@@ -227,7 +227,7 @@
 			if ((object)item != null)
 			{
 				ItemDrop component = item.GetComponent<ItemDrop>();
-				if ((object)component != null && component.m_itemData.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Consumable && component.m_itemData.m_shared.m_food > 0f)
+				if ((object)component != null && component.m_itemData.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Consumable && component.m_itemData.m_shared.m_food > 0f && !itemsExcluded.Contains(item))
 				{
 					stringBuilder.Append($"\n{component.m_itemData.m_shared.m_name}. FoodAmount: {component.m_itemData.m_shared.m_food}");
 					m_foodItems.Add(component);
```
