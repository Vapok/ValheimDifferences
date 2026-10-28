# `CookingStation.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+35/-10` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `DropAllItems() [Method Body Modified]`
- `GetFuel() [Method Body Modified]`
- `RPC_AddItem() [Method Body Modified]`
- `RPC_RemoveDoneItem() [Method Body Modified]`
- `SetSlot() [Method Body Modified]`
- `SetSlot() [Method Removed]`
- `SpawnItem() [Method Body Modified]`
- `UpdateCooking() [Method Body Modified]`
- `private void SetSlot(int slot, string itemName, float cookedTime, Status status, bool cheated)`
- `private void SetSlot(int slot, string itemName, float cookedTime, Status status, bool cheated, long sender = 0L)`

---

## 📝 Code Diff

```diff
--- a/CookingStation.cs
+++ b/CookingStation.cs
@@ -217,7 +217,7 @@
 				break;
 			}
 			}
-			SetSlot(j, "", 0f, Status.NotDone, cheated: false);
+			SetSlot(j, "", 0f, Status.NotDone, cheated: false, 0L);
 		}
 		void drop(ItemDrop item, bool flag)
 		{
@@ -260,23 +260,23 @@
 					ItemConversion itemConversion = GetItemConversion(itemName);
 					if (itemConversion == null)
 					{
-						SetSlot(i, "", 0f, Status.NotDone, cheated);
+						SetSlot(i, "", 0f, Status.NotDone, cheated, 0L);
 						continue;
 					}
 					cookedTime += deltaTime;
 					if (m_canOvercookItems && cookedTime > itemConversion.m_cookTime * 2f)
 					{
 						m_overcookedEffect.Create(m_slots[i].position, Quaternion.identity);
-						SetSlot(i, m_overCookedItem.name, cookedTime, Status.Burnt, cheated);
+						SetSlot(i, m_overCookedItem.name, cookedTime, Status.Burnt, cheated, 0L);
 					}
 					else if (cookedTime > itemConversion.m_cookTime && itemName == itemConversion.m_from.name)
 					{
 						m_doneEffect.Create(m_slots[i].position, Quaternion.identity);
-						SetSlot(i, itemConversion.m_to.name, cookedTime, Status.Done, cheated);
+						SetSlot(i, itemConversion.m_to.name, cookedTime, Status.Done, cheated, 0L);
 					}
 					else
 					{
-						SetSlot(i, itemName, cookedTime, status, cheated);
+						SetSlot(i, itemName, cookedTime, status, cheated, 0L);
 					}
 				}
 			}
@@ -445,7 +445,7 @@
 				{
 					SpawnItem(itemName, i, userPoint, cheated);
 				}
-				SetSlot(i, "", 0f, Status.NotDone, cheated: false);
+				SetSlot(i, "", 0f, Status.NotDone, cheated: false, 0L);
 				m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetSlotVisual", i, "");
 				break;
 			}
@@ -538,8 +538,25 @@
 		}
 		if (m_recordCrafter)
 		{
-			component.m_itemData.m_crafterID = Player.m_localPlayer.GetPlayerID();
-			component.m_itemData.m_crafterName = Player.m_localPlayer.GetPlayerName();
+			long num = m_nview.GetZDO().GetLong(ZDOVars.s_playerID + slot, 0L);
+			if (num != 0L)
+			{
+				foreach (ZNet.PlayerInfo player in ZNet.instance.GetPlayerList())
+				{
+					ZDOID characterID = player.m_characterID;
+					if (characterID.UserID == num)
+					{
+						component.m_itemData.m_crafterID = num;
+						component.m_itemData.m_crafterName = player.m_name;
+						break;
+					}
+				}
+			}
+			else
+			{
+				component.m_itemData.m_crafterID = Player.m_localPlayer.GetPlayerID();
+				component.m_itemData.m_crafterName = Player.m_localPlayer.GetPlayerName();
+			}
 		}
 		gameObject.GetComponent<Rigidbody>().linearVelocity = vector2 * m_spawnForce;
 		m_pickEffector.Create(vector, Quaternion.identity);
@@ -810,14 +827,14 @@
 			int freeSlot = GetFreeSlot();
 			if (freeSlot != -1)
 			{
-				SetSlot(freeSlot, itemName, 0f, Status.NotDone, cheated);
+				SetSlot(freeSlot, itemName, 0f, Status.NotDone, cheated, sender);
 				m_nview.InvokeRPC(ZNetView.Everybody, "RPC_SetSlotVisual", freeSlot, itemName);
 				m_addEffect.Create(m_slots[freeSlot].position, Quaternion.identity);
 			}
 		}
 	}
 
-	private void SetSlot(int slot, string itemName, float cookedTime, Status status, bool cheated)
+	private void SetSlot(int slot, string itemName, float cookedTime, Status status, bool cheated, long sender = 0L)
 	{
 		if (m_nview.IsValid())
 		{
@@ -825,6 +842,10 @@
 			m_nview.GetZDO().Set("slot" + slot, cookedTime);
 			m_nview.GetZDO().Set("slotstatus" + slot, (int)status);
 			m_nview.GetZDO().Set(ZDOVars.s_cheatedQueued + slot, cheated);
+			if (sender != 0L)
+			{
+				m_nview.GetZDO().Set(ZDOVars.s_playerID + slot, sender);
+			}
 		}
 	}
 
@@ -906,6 +927,10 @@
 
 	private float GetFuel()
 	{
+		if (!(m_nview != null) || !m_nview.IsValid())
+		{
+			return 0f;
+		}
 		return m_nview.GetZDO().GetFloat(ZDOVars.s_fuel);
 	}
 
```
