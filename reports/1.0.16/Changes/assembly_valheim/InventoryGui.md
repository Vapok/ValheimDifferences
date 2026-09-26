# `InventoryGui.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+25/-17` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InventoryGui.cs
+++ b/InventoryGui.cs
@@ -398,10 +398,10 @@
 		InventoryGrid containerGrid7 = m_containerGrid;
 		containerGrid7.CanDropDragOntoItem = (Func<ItemDrop.ItemData, bool>)Delegate.Combine(containerGrid7.CanDropDragOntoItem, new Func<ItemDrop.ItemData, bool>(CanDropDragOntoItem));
 		UIDragHandler component = m_dropButton.GetComponent<UIDragHandler>();
-		component.m_onReleasedOn = (Action<UIDragHandler>)Delegate.Combine(component.m_onReleasedOn, (Action<UIDragHandler>)delegate
+		component.m_onReleasedOn = (Action<UIDragHandler>)Delegate.Combine(component.m_onReleasedOn, (Action<UIDragHandler>)((UIDragHandler _) =>
 		{
 			OnDropOutside();
-		});
+		}));
 		m_craftButton.onClick.AddListener(OnCraftPressed);
 		m_craftCancelButton.onClick.AddListener(OnCraftCancelPressed);
 		m_dropButton.onClick.AddListener(OnDropOutside);
@@ -851,7 +851,7 @@
 			}
 			if (Player.m_localPlayer.DropItem(m_dragInventory, m_dragItem, m_dragAmount))
 			{
-				m_moveItemEffects.Create(base.transform.position, Quaternion.identity);
+				m_moveItemEffects.Create(transform.position, Quaternion.identity);
 				SetupDragItem(null, null, 1);
 				UpdateCraftingPanel();
 			}
@@ -881,7 +881,7 @@
 		SetActiveGroup(grid.m_uiGroup, playSound: false);
 		if ((bool)m_dragGo)
 		{
-			m_moveItemEffects.Create(base.transform.position, Quaternion.identity);
+			m_moveItemEffects.Create(transform.position, Quaternion.identity);
 			bool flag = localPlayer.IsItemEquiped(m_dragItem);
 			bool flag2 = item != null && localPlayer.IsItemEquiped(item);
 			Vector2i gridPos = m_dragItem.m_gridPos;
@@ -963,17 +963,17 @@
 					{
 						m_currentContainer.GetInventory().MoveItemToThis(localPlayer.GetInventory(), item);
 					}
-					m_moveItemEffects.Create(base.transform.position, Quaternion.identity);
+					m_moveItemEffects.Create(transform.position, Quaternion.identity);
 				}
 				else if (Player.m_localPlayer.DropItem(grid.GetInventory(), item, item.m_stack))
 				{
-					m_moveItemEffects.Create(base.transform.position, Quaternion.identity);
+					m_moveItemEffects.Create(transform.position, Quaternion.identity);
 				}
 				return;
 			case InventoryGrid.Modifier.Drop:
 				if (Player.m_localPlayer.DropItem(grid.GetInventory(), item, item.m_stack))
 				{
-					m_moveItemEffects.Create(base.transform.position, Quaternion.identity);
+					m_moveItemEffects.Create(transform.position, Quaternion.identity);
 				}
 				return;
 			case InventoryGrid.Modifier.Split:
@@ -1223,7 +1223,7 @@
 		switch (sortMethod)
 		{
 		case SortMethod.Original:
-			m_availableRecipes.Sort(delegate(RecipeDataPair a, RecipeDataPair b2)
+			m_availableRecipes.Sort((RecipeDataPair a, RecipeDataPair b2) =>
 			{
 				int num2 = byCraftable(a, b2);
 				if (num2 == 0)
@@ -1242,7 +1242,7 @@
 			});
 			break;
 		case SortMethod.Name:
-			m_availableRecipes.Sort(delegate(RecipeDataPair a, RecipeDataPair b2)
+			m_availableRecipes.Sort((RecipeDataPair a, RecipeDataPair b2) =>
 			{
 				int num2 = byCraftable(a, b2);
 				if (num2 == 0)
@@ -1261,7 +1261,7 @@
 			});
 			break;
 		case SortMethod.Type:
-			m_availableRecipes.Sort(delegate(RecipeDataPair a, RecipeDataPair b2)
+			m_availableRecipes.Sort((RecipeDataPair a, RecipeDataPair b2) =>
 			{
 				int num2 = byCraftable(a, b2);
 				if (num2 == 0)
@@ -1284,7 +1284,7 @@
 			});
 			break;
 		case SortMethod.Weight:
-			m_availableRecipes.Sort(delegate(RecipeDataPair a, RecipeDataPair b2)
+			m_availableRecipes.Sort((RecipeDataPair a, RecipeDataPair b2) =>
 			{
 				int num2 = byCraftable(a, b2);
 				if (num2 == 0)
@@ -1370,7 +1370,7 @@
 		{
 			component4.gameObject.SetActive(value: false);
 		}
-		element.GetComponent<Button>().onClick.AddListener(delegate
+		element.GetComponent<Button>().onClick.AddListener(() =>
 		{
 			OnSelectedRecipe(element);
 		});
@@ -1455,7 +1455,7 @@
 		}
 		if (index < 0)
 		{
-			m_selectedRecipe = default(RecipeDataPair);
+			m_selectedRecipe = default;
 			m_selectedVariant = 0;
 			return;
 		}
@@ -1614,7 +1614,15 @@
 			m_craftButton.gameObject.SetActive(value: true);
 			return;
 		}
-		float num6 = (flag ? (m_upgraderDuration + (float)num * m_upgraderDurationPerLevel) : (m_multiCrafting ? m_multiCraftDuration : m_craftDuration));
+		float num6;
+		if (flag)
+		{
+			num6 = m_upgraderDuration + (float)num * m_upgraderDurationPerLevel;
+		}
+		else
+		{
+			num6 = (m_multiCrafting ? m_multiCraftDuration : m_craftDuration);
+		}
 		if (currentCraftingStation != null && currentCraftingStation.m_craftingSkill != Skills.SkillType.None)
 		{
 			num6 *= 1f - Player.m_localPlayer.GetSkillFactor(currentCraftingStation.m_craftingSkill) * m_craftDurationSkillMaxDecrease;
@@ -2238,11 +2246,11 @@
 		}
 		if (item != null)
 		{
-			m_dragGo = UnityEngine.Object.Instantiate(m_dragItemPrefab, base.transform);
+			m_dragGo = UnityEngine.Object.Instantiate(m_dragItemPrefab, transform);
 			m_dragItem = item;
 			m_dragInventory = inventory;
 			m_dragAmount = amount;
-			m_moveItemEffects.Create(base.transform.position, Quaternion.identity);
+			m_moveItemEffects.Create(transform.position, Quaternion.identity);
 			if (!ZInput.IsTouchActive())
 			{
 				UITooltip.HideTooltip();
@@ -2470,7 +2478,7 @@
 			Button component = rectTransform.GetComponent<Button>();
 			if (clickable)
 			{
-				component.onClick.AddListener(delegate
+				component.onClick.AddListener(() =>
 				{
 					achievementsGui.OnOpenAchievementDetails(item, clickable);
 				});
```
