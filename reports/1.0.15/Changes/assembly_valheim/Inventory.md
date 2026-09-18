# `Inventory.cs` Diff (`1.0.14` $\rightarrow$ `1.0.15`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Inventory.cs
+++ b/Inventory.cs
@@ -117,10 +117,14 @@
 		{
 			for (int i = 0; i < item.m_stack; i++)
 			{
-				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel, item.m_cheated);
+				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel);
 				if (itemData != null)
 				{
 					itemData.m_stack++;
+					if (item.m_cheated && !PlayerProfile.s_bypassCheatChecks)
+					{
+						itemData.m_cheated = true;
+					}
 					continue;
 				}
 				int stack = item.m_stack - i;
@@ -165,7 +169,7 @@
 		{
 			for (int i = 0; i < item.m_stack; i++)
 			{
-				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel, item.m_cheated);
+				ItemDrop.ItemData itemData = FindFreeStackItem(item.m_shared.m_name, item.m_quality, item.m_worldLevel);
 				if (itemData != null)
 				{
 					itemData.m_stack++;
@@ -540,11 +544,11 @@
 		return num;
 	}
 
-	private ItemDrop.ItemData FindFreeStackItem(string name, int quality, float worldLevel, bool cheated)
-	{
-		foreach (ItemDrop.ItemData item in m_inventory)
-		{
-			if (item.m_shared.m_name == name && item.m_quality == quality && item.m_stack < item.m_shared.m_maxStackSize && (float)item.m_worldLevel == worldLevel && item.m_cheated == cheated)
+	private ItemDrop.ItemData FindFreeStackItem(string name, int quality, float worldLevel)
+	{
+		foreach (ItemDrop.ItemData item in m_inventory)
+		{
+			if (item.m_shared.m_name == name && item.m_quality == quality && item.m_stack < item.m_shared.m_maxStackSize && (float)item.m_worldLevel == worldLevel)
 			{
 				return item;
 			}
```
