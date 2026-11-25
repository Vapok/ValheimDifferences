# `CookingStation.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+15/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Awake() [Method Body Modified]`
- `GetHoverText() [Method Body Modified]`
- `RPC_SetCrafterStat() [Method Body Modified]`
- `SpawnItem() [Method Body Modified]`
- `private void RPC_SetCrafterStat(long sender, long crafterId, string itemName)`

---

## 📝 Code Diff

```diff
--- a/CookingStation.cs
+++ b/CookingStation.cs
@@ -156,6 +156,7 @@
 			m_nview.Register<string, bool>("RPC_AddItem", RPC_AddItem);
 			m_nview.Register("RPC_AddFuel", RPC_AddFuel);
 			m_nview.Register<int, string>("RPC_SetSlotVisual", RPC_SetSlotVisual);
+			m_nview.Register<long, string>("RPC_SetCrafterStat", RPC_SetCrafterStat);
 			if ((bool)m_addFoodSwitch)
 			{
 				m_addFoodSwitch.m_onUse = OnAddFoodSwitch;
@@ -536,6 +537,7 @@
 		{
 			component.m_itemData.m_durability = component.m_itemData.m_shared.m_maxDurability;
 		}
+		bool flag = false;
 		if (m_recordCrafter)
 		{
 			long num = m_nview.GetZDO().GetLong(ZDOVars.s_playerID + slot, 0L);
@@ -546,21 +548,30 @@
 					ZDOID characterID = player.m_characterID;
 					if (characterID.UserID == num)
 					{
+						flag = true;
 						component.m_itemData.m_crafterID = num;
 						component.m_itemData.m_crafterName = player.m_name;
+						m_nview.InvokeRPC(num, "RPC_SetCrafterStat", num, component.m_itemData.m_shared.m_name);
 						break;
 					}
 				}
 			}
-			else
-			{
-				component.m_itemData.m_crafterID = Player.m_localPlayer.GetPlayerID();
+			if (!flag)
+			{
+				component.m_itemData.m_crafterID = ZNet.GetUID();
 				component.m_itemData.m_crafterName = Player.m_localPlayer.GetPlayerName();
 			}
 		}
 		gameObject.GetComponent<Rigidbody>().linearVelocity = vector2 * m_spawnForce;
 		m_pickEffector.Create(vector, Quaternion.identity);
-		Game.instance.GetPlayerProfile().IncrementStatItemCraft(component.m_itemData.m_shared.m_name);
+	}
+
+	private void RPC_SetCrafterStat(long sender, long crafterId, string itemName)
+	{
+		if (crafterId == ZNet.GetUID())
+		{
+			Game.instance.GetPlayerProfile().IncrementStatItemCraft(itemName);
+		}
 	}
 
 	public string GetHoverText()
```
