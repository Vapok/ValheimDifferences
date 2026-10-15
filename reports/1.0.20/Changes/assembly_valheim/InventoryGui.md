# `InventoryGui.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/InventoryGui.cs
+++ b/InventoryGui.cs
@@ -1832,7 +1832,7 @@
 		long playerID = player.GetPlayerID();
 		string playerName = player.GetPlayerName();
 		bool flag2 = player.GetInventory().ItemCheated(m_craftRecipe.m_resources) || player.NoCostCheat();
-		bool flag3 = currentCraftingStation?.GetComponent<ZNetView>().GetZDO().GetBool(ZDOVars.s_cheated) ?? false;
+		bool flag3 = currentCraftingStation?.GetComponent<ZNetView>().GetZDO().IsCheated() ?? false;
 		bool cheated = (flag2 | flag3) && !PlayerProfile.s_bypassCheatChecks;
 		ItemDrop.ItemData itemData = null;
 		bool flag4 = false;
@@ -1854,15 +1854,19 @@
 				ZLog.LogError("No upgrader resource found in inventory");
 				return;
 			}
-			float num5 = UnityEngine.Random.Range(0f, 1f);
-			if (itemData2.m_shared.m_upgradeChance >= num5)
+			float itemUpgradeChance = Player.m_localPlayer.GetItemUpgradeChance(m_craftRecipe.m_item.gameObject.name.GetStableHashCode() + num);
+			if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("upgrader"))
+			{
+				ZLog.Log($"Upgrader RNG: {m_craftRecipe.m_item.gameObject.name}: {itemUpgradeChance}");
+			}
+			if (itemData2.m_shared.m_upgradeChance >= itemUpgradeChance)
 			{
 				ZLog.Log($"Upgrader <color=yellow>succeeded</color> on {m_craftUpgradeItem.m_shared.m_name} level {num}!");
 				player.Message(MessageHud.MessageType.Center, Localization.instance.Localize("$msg_upgrader_success", m_craftUpgradeItem.m_shared.m_name, num.ToString()), 0, null, log: true);
 				itemData = player.GetInventory().AddItem(m_craftRecipe.m_item.gameObject.name, num3, num, variant, playerID, playerName, position, cheated);
 				flag4 = true;
 			}
-			else if (itemData2.m_shared.m_breakChance >= 1f - num5)
+			else if (itemData2.m_shared.m_breakChance >= 1f - itemUpgradeChance)
 			{
 				ZLog.Log($"Upgrader <color=red>BROKE</color> {m_craftUpgradeItem.m_shared.m_name} level {num - 1} and was destroyed!");
 				player.Message(MessageHud.MessageType.Center, Localization.instance.Localize("$msg_upgrader_broke", m_craftUpgradeItem.m_shared.m_name, (num - 1).ToString()), 0, null, log: true);
@@ -1873,11 +1877,11 @@
 					{
 						if (requirement2.m_recover)
 						{
-							int num6 = Mathf.CeilToInt((float)(requirement2.GetAmount(1) + requirement2.GetAmount(num - 1)) * itemData2.m_shared.m_breakReturnIngreientsAmount);
-							if (num6 > 0)
+							int num5 = Mathf.CeilToInt((float)(requirement2.GetAmount(1) + requirement2.GetAmount(num - 1)) * itemData2.m_shared.m_breakReturnIngreientsAmount);
+							if (num5 > 0)
 							{
-								itemData = player.GetInventory().AddItem(requirement2.m_resItem.name, num6, requirement2.m_resItem.m_itemData.m_quality, requirement2.m_resItem.m_itemData.m_variant, playerID, playerName, new Vector2i(-1, -1), cheated);
-								ZLog.Log($"Upgrader returned {requirement2.m_resItem.m_itemData.m_shared.m_name} x{num6} to inventory");
+								itemData = player.GetInventory().AddItem(requirement2.m_resItem.name, num5, requirement2.m_resItem.m_itemData.m_quality, requirement2.m_resItem.m_itemData.m_variant, playerID, playerName, new Vector2i(-1, -1), cheated);
+								ZLog.Log($"Upgrader returned {requirement2.m_resItem.m_itemData.m_shared.m_name} x{num5} to inventory");
 							}
 						}
 					}
```
