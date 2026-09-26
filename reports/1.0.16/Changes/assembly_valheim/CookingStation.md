# `CookingStation.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+20/-20` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CookingStation.cs
+++ b/CookingStation.cs
@@ -141,7 +141,7 @@
 
 	private void Awake()
 	{
-		m_nview = base.gameObject.GetComponent<ZNetView>();
+		m_nview = gameObject.GetComponent<ZNetView>();
 		if (m_nview.GetZDO() != null)
 		{
 			m_moveObjectDynamics = new FloatDynamics(m_moveObjectParameters, 0f);
@@ -221,7 +221,7 @@
 		}
 		void drop(ItemDrop item, bool flag)
 		{
-			Vector3 position = base.transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
+			Vector3 position = transform.position + Vector3.up + UnityEngine.Random.insideUnitSphere * 0.3f;
 			Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 			GameObject go = UnityEngine.Object.Instantiate(item.gameObject, position, rotation);
 			flag |= m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
@@ -290,7 +290,7 @@
 
 	private void Update()
 	{
-		if (!Player.IsPlacementGhost(base.gameObject) && m_moveObjectWhileCooking)
+		if (!Player.IsPlacementGhost(gameObject) && m_moveObjectWhileCooking)
 		{
 			float target = ((IsStationFull() && !IsEverythingCooked() && GetFuel() > 0f) ? 1f : 0f);
 			float t = m_moveObjectDynamics.Update(Time.deltaTime, target);
@@ -313,7 +313,7 @@
 
 	private bool IsStationFull()
 	{
-		if (Player.IsPlacementGhost(base.gameObject))
+		if (Player.IsPlacementGhost(gameObject))
 		{
 			return false;
 		}
@@ -424,9 +424,9 @@
 				transform = itemPrefab.transform.Find("attach");
 			}
 			Transform transform2 = m_slots[i];
-			GameObject obj = UnityEngine.Object.Instantiate(transform.gameObject, transform2.position, transform2.rotation, transform2);
-			obj.name = item;
-			Renderer[] componentsInChildren = obj.GetComponentsInChildren<Renderer>();
+			GameObject gameObject = UnityEngine.Object.Instantiate(transform.gameObject, transform2.position, transform2.rotation, transform2);
+			gameObject.name = item;
+			Renderer[] componentsInChildren = gameObject.GetComponentsInChildren<Renderer>();
 			for (int j = 0; j < componentsInChildren.Length; j++)
 			{
 				componentsInChildren[j].shadowCastingMode = ShadowCastingMode.Off;
@@ -529,8 +529,8 @@
 			vector2 = vector3;
 		}
 		Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
-		GameObject obj = UnityEngine.Object.Instantiate(itemPrefab, vector, rotation);
-		ItemDrop component = obj.GetComponent<ItemDrop>();
+		GameObject gameObject = UnityEngine.Object.Instantiate(itemPrefab, vector, rotation);
+		ItemDrop component = gameObject.GetComponent<ItemDrop>();
 		ItemDrop.OnCreateNew(component, cheated);
 		if (m_spawnFullDurability && (bool)component)
 		{
@@ -541,7 +541,7 @@
 			component.m_itemData.m_crafterID = Player.m_localPlayer.GetPlayerID();
 			component.m_itemData.m_crafterName = Player.m_localPlayer.GetPlayerName();
 		}
-		obj.GetComponent<Rigidbody>().linearVelocity = vector2 * m_spawnForce;
+		gameObject.GetComponent<Rigidbody>().linearVelocity = vector2 * m_spawnForce;
 		m_pickEffector.Create(vector, Quaternion.identity);
 		Game.instance.GetPlayerProfile().IncrementStatItemCraft(component.m_itemData.m_shared.m_name);
 	}
@@ -599,7 +599,7 @@
 			ZLog.Log("Add fuel");
 			float fuel = GetFuel();
 			SetFuel(fuel + 1f);
-			m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation, base.transform);
+			m_fuelAddedEffects.Create(transform.position, transform.rotation, transform);
 		}
 	}
 
@@ -607,7 +607,7 @@
 	{
 		float fuel = GetFuel();
 		Localization instance = Localization.instance;
-		string[] obj = new string[9]
+		string[] array = new string[9]
 		{
 			m_name,
 			" (",
@@ -620,10 +620,10 @@
 			null
 		};
 		int maxFuel = m_maxFuel;
-		obj[6] = maxFuel.ToString();
-		obj[7] = ")\n[<color=yellow><b>$KEY_Use</b></color>] $piece_smelter_add ";
-		obj[8] = m_fuelItem.m_itemData.m_shared.m_name;
-		return instance.Localize(string.Concat(obj));
+		array[6] = maxFuel.ToString();
+		array[7] = ")\n[<color=yellow><b>$KEY_Use</b></color>] $piece_smelter_add ";
+		array[8] = m_fuelItem.m_itemData.m_shared.m_name;
+		return instance.Localize(string.Concat(array));
 	}
 
 	private bool OnAddFoodSwitch(Switch caller, Humanoid user, ItemDrop.ItemData item)
@@ -662,10 +662,10 @@
 			if (m_canGiveBonusYield && UnityEngine.Random.value < skillFactor * InventoryGui.instance.m_craftBonusChance)
 			{
 				num += InventoryGui.instance.m_craftBonusAmount;
-				DamageText.instance.ShowText(DamageText.TextType.Bonus, base.transform.position + Vector3.up, "+" + InventoryGui.instance.m_craftBonusAmount, player: true);
-				InventoryGui.instance.m_craftBonusEffect.Create(base.transform.position, Quaternion.identity);
+				DamageText.instance.ShowText(DamageText.TextType.Bonus, transform.position + Vector3.up, "+" + InventoryGui.instance.m_craftBonusAmount, player: true);
+				InventoryGui.instance.m_craftBonusEffect.Create(transform.position, Quaternion.identity);
 				Game.instance.IncrementPlayerStat(m_bonusStat);
-				ZLog.Log("Bonus from cooking station! " + base.gameObject.name);
+				ZLog.Log("Bonus from cooking station! " + gameObject.name);
 			}
 			Game.instance.IncrementPlayerStat((NextItemStatus() == Status.Done) ? m_cookStat : m_burntStat);
 			m_nview.InvokeRPC("RPC_RemoveDoneItem", user.transform.position, num);
@@ -1002,7 +1002,7 @@
 		else
 		{
 			Gizmos.color = Color.red;
-			Gizmos.DrawWireSphere(base.transform.position, m_fireCheckRadius);
+			Gizmos.DrawWireSphere(transform.position, m_fireCheckRadius);
 		}
 	}
 
```
