# `Inventory.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-15` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Inventory.cs
+++ b/Inventory.cs
@@ -117,14 +117,10 @@
 		{
 			for (int i = 0; i < item.m_stack; i++)
 			{
-				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel);
+				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel, item.m_cheated);
 				if (itemData != null)
 				{
 					itemData.m_stack++;
-					if (item.m_cheated && !PlayerProfile.s_bypassCheatChecks)
-					{
-						itemData.m_cheated = true;
-					}
 					continue;
 				}
 				int stack = item.m_stack - i;
@@ -138,7 +134,7 @@
 				else
 				{
 					flag = false;
-					ZLog.LogError($"Trying to add item to occupied slot {gridPos.x}, {gridPos.y}");
+					ZLog.LogWarning($"Trying to add item to occupied slot {gridPos.x}, {gridPos.y}");
 				}
 				break;
 			}
@@ -154,7 +150,7 @@
 			else
 			{
 				flag = false;
-				ZLog.LogError($"Trying to add item to occupied slot {gridPos2.x}, {gridPos2.y}");
+				ZLog.LogWarning($"Trying to add item to occupied slot {gridPos2.x}, {gridPos2.y}");
 			}
 		}
 		Changed(flag, cheatedStateChanged);
@@ -169,7 +165,7 @@
 		{
 			for (int i = 0; i < item.m_stack; i++)
 			{
-				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel);
+				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel, item.m_cheated);
 				if (itemData != null)
 				{
 					itemData.m_stack++;
@@ -185,7 +181,7 @@
 				else
 				{
 					flag = false;
-					ZLog.LogError($"Trying to add item to occupied slot {pos.x}, {pos.y}");
+					ZLog.LogWarning($"Trying to add item to occupied slot {pos.x}, {pos.y}");
 				}
 				break;
 			}
@@ -198,7 +194,7 @@
 		else
 		{
 			flag = false;
-			ZLog.LogError($"Trying to add item to occupied slot {pos.x}, {pos.y}");
+			ZLog.LogWarning($"Trying to add item to occupied slot {pos.x}, {pos.y}");
 		}
 		Changed(flag, cheatedStateChanged);
 		return flag;
@@ -544,11 +540,11 @@
 		return num;
 	}
 
-	private ItemDrop.ItemData FindFreeStackItem(string name, int quality, float worldLevel)
-	{
-		foreach (ItemDrop.ItemData item in m_inventory)
-		{
-			if (item.m_shared.m_name == name && item.m_quality == quality && item.m_stack < item.m_shared.m_maxStackSize && (float)item.m_worldLevel == worldLevel)
+	private ItemDrop.ItemData FindFreeStackItem(string name, int quality, float worldLevel, bool cheated)
+	{
+		foreach (ItemDrop.ItemData item in m_inventory)
+		{
+			if (item.m_shared.m_name == name && item.m_quality == quality && item.m_stack < item.m_shared.m_maxStackSize && (float)item.m_worldLevel == worldLevel && item.m_cheated == cheated)
 			{
 				return item;
 			}
```
