# `Achievements.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Achievements.cs
+++ b/Achievements.cs
@@ -95,6 +95,10 @@
 	[Header("Items excluded from crafting-related achievements")]
 	[Tooltip("For various reasons, some items may be implemented with recipes in the game, but are not normally craftable - they should be excluded here.")]
 	public List<GameObject> m_itemsExcluded = new List<GameObject>();
+
+	[Header("Items excluded from consumable-related achievements")]
+	[Tooltip("For various reasons, some items may be in the game, but not consumable - they should be excluded here.")]
+	public List<GameObject> m_consumablesExcluded = new List<GameObject>();
 
 	public GameObject m_unlockAchievementPopup;
 
@@ -411,7 +415,8 @@
 		{
 			foreach (Achievement achievement in achievementList.m_achievements)
 			{
-				if (achievement.m_id != calleeId && achievement.m_otherAchievementTriggers.Count > 0 && achievement.CheckUnlocked() && !achievement.m_unlocked)
+				bool unlocked = achievement.m_unlocked;
+				if (achievement.m_id != calleeId && achievement.m_otherAchievementTriggers.Count > 0 && achievement.CheckUnlocked() && !unlocked)
 				{
 					AchievementEvent(achievement);
 				}
@@ -463,7 +468,7 @@
 						SetupDynamicAchievement(achievement, GetCraftableItems(ObjectDB.instance.m_recipes), achievement.m_itemCraftTriggers, (ItemDrop item) => item?.m_itemData?.m_shared?.m_name);
 						break;
 					case "AllFoodEaten":
-						SetupDynamicAchievement(achievement, ObjectDB.instance.GetAllFoodItems(), achievement.m_foodEatenTriggers, (ItemDrop item) => item.m_itemData.m_shared.m_name);
+						SetupDynamicAchievement(achievement, ObjectDB.instance.GetAllFoodItems(m_consumablesExcluded), achievement.m_foodEatenTriggers, (ItemDrop item) => item?.m_itemData?.m_shared?.m_name);
 						break;
 					case "AllBuildPieces":
 						SetupDynamicAchievement(achievement, ObjectDB.instance.GetAllBuildPieces(includeHidden: true), achievement.m_piecePlacedTriggers, (Piece piece) => piece.m_name);
```
