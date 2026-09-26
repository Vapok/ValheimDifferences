# `OfferingBowl.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/OfferingBowl.cs
+++ b/OfferingBowl.cs
@@ -169,7 +169,7 @@
 					user.GetInventory().RemoveItem(item.m_shared.m_name, m_bossItems);
 					user.ShowRemovedMessage(m_bossItem.m_itemData, m_bossItems);
 					user.Message(MessageHud.MessageType.Center, m_usedAltarText);
-					m_fuelAddedEffects.Create(m_itemSpawnPoint.position, base.transform.rotation);
+					m_fuelAddedEffects.Create(m_itemSpawnPoint.position, transform.rotation);
 				}
 				if (!string.IsNullOrEmpty(m_setGlobalKey))
 				{
@@ -200,8 +200,8 @@
 		{
 			return m_spawnPoints[Random.Range(0, m_spawnPoints.Count)].transform.position;
 		}
-		Vector3 vector = base.transform.localToWorldMatrix * m_spawnAreaOffset;
-		return base.transform.position + vector;
+		Vector3 vector = transform.localToWorldMatrix * m_spawnAreaOffset;
+		return transform.position + vector;
 	}
 
 	private void InitiateSpawnBoss(Vector3 point, bool removeItemsFromInventory)
@@ -251,7 +251,7 @@
 		m_interactUser.Message(MessageHud.MessageType.Center, m_usedAltarText);
 		if ((bool)m_itemSpawnPoint)
 		{
-			m_fuelAddedEffects.Create(m_itemSpawnPoint.position, base.transform.rotation);
+			m_fuelAddedEffects.Create(m_itemSpawnPoint.position, transform.rotation);
 		}
 	}
 
@@ -263,7 +263,7 @@
 		}
 		if ((bool)m_itemSpawnPoint)
 		{
-			m_fuelAddedEffects.Create(m_itemSpawnPoint.position, base.transform.rotation);
+			m_fuelAddedEffects.Create(m_itemSpawnPoint.position, transform.rotation);
 		}
 	}
 
@@ -282,7 +282,7 @@
 			if (m_enableSolidHeightCheck)
 			{
 				ZoneSystem.instance.GetSolidHeight(spawnPoint, out var height, m_getSolidHeightMargin);
-				if (height < 0f || Mathf.Abs(height - base.transform.position.y) > m_spawnBossMaxYDistance || Vector3.Distance(spawnPoint, point) < m_spawnBossMinDistance)
+				if (height < 0f || Mathf.Abs(height - transform.position.y) > m_spawnBossMaxYDistance || Vector3.Distance(spawnPoint, point) < m_spawnBossMinDistance)
 				{
 					continue;
 				}
@@ -346,7 +346,7 @@
 		ItemStand[] array = Object.FindObjectsOfType<ItemStand>();
 		foreach (ItemStand itemStand in array)
 		{
-			if (!(Vector3.Distance(base.transform.position, itemStand.transform.position) > m_itemstandMaxRange) && itemStand.gameObject.name.CustomStartsWith(m_itemStandPrefix))
+			if (!(Vector3.Distance(transform.position, itemStand.transform.position) > m_itemstandMaxRange) && itemStand.gameObject.name.CustomStartsWith(m_itemStandPrefix))
 			{
 				list.Add(itemStand);
 			}
```
