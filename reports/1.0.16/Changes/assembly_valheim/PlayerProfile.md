# `PlayerProfile.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlayerProfile.cs
+++ b/PlayerProfile.cs
@@ -931,7 +931,7 @@
 
 	private void LogFoodsConsumed()
 	{
-		List<ItemDrop> edibleFoods = ObjectDB.instance.GetAllFoodItems();
+		List<ItemDrop> edibleFoods = ObjectDB.instance.GetAllFoodItems(Achievements.m_instance.m_consumablesExcluded);
 		int num = m_playerStats[Achievements.GetCurrentAchievementDifficultyIndex()].m_foodEatenStats.Count((KeyValuePair<string, float> kvp) => edibleFoods.Any((ItemDrop r) => r.m_itemData.m_shared.m_name == kvp.Key));
 		float num2 = (float)num / (float)edibleFoods.Count;
 		ZLog.Log($"{num} Food items consumed.{num2 * 100f}% of all {edibleFoods.Count} food items.");
```
