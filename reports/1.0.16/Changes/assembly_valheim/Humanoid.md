# `Humanoid.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+28/-28` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Humanoid.cs
+++ b/Humanoid.cs
@@ -655,7 +655,7 @@
 		{
 			EquipItem(component.m_itemData);
 		}
-		m_pickupEffects.Create(base.transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
+		m_pickupEffects.Create(transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
 		if (IsPlayer())
 		{
 			ShowPickupMessage(component.m_itemData, stack);
@@ -678,11 +678,11 @@
 		if ((bool)targetCreature)
 		{
 			float radius = targetCreature.GetRadius();
-			num = Vector3.Distance(targetCreature.transform.position, base.transform.position) - radius;
+			num = Vector3.Distance(targetCreature.transform.position, transform.position) - radius;
 		}
 		else if ((bool)targetStatic)
 		{
-			num = Vector3.Distance(targetStatic.transform.position, base.transform.position);
+			num = Vector3.Distance(targetStatic.transform.position, transform.position);
 		}
 		float time = Time.time;
 		IsFlying();
@@ -856,7 +856,7 @@
 			ZLog.Log("drop some " + amount + "  " + item.m_stack);
 			inventory.RemoveItem(item, amount);
 		}
-		ItemDrop itemDrop = ItemDrop.DropItem(item, amount, base.transform.position + base.transform.forward + base.transform.up, base.transform.rotation);
+		ItemDrop itemDrop = ItemDrop.DropItem(item, amount, transform.position + transform.forward + transform.up, transform.rotation);
 		if (IsPlayer())
 		{
 			itemDrop.OnPlayerDrop();
@@ -866,9 +866,9 @@
 		{
 			num = 0.5f;
 		}
-		itemDrop.GetComponent<Rigidbody>().linearVelocity = (base.transform.forward + Vector3.up) * num;
+		itemDrop.GetComponent<Rigidbody>().linearVelocity = (transform.forward + Vector3.up) * num;
 		m_zanim.SetTrigger("interact");
-		m_dropEffects.Create(base.transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
+		m_dropEffects.Create(transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
 		Message(MessageHud.MessageType.TopLeft, "$msg_dropped " + itemDrop.m_itemData.m_shared.m_name, itemDrop.m_itemData.m_stack, itemDrop.m_itemData.GetIcon());
 		return true;
 	}
@@ -965,10 +965,10 @@
 
 	protected void DoInteractAnimation(GameObject obj)
 	{
-		Vector3 forward = obj.transform.position - base.transform.position;
+		Vector3 forward = obj.transform.position - transform.position;
 		forward.y = 0f;
 		forward.Normalize();
-		base.transform.rotation = Quaternion.LookRotation(forward);
+		transform.rotation = Quaternion.LookRotation(forward);
 		Physics.SyncTransforms();
 		ItemDrop component = obj.GetComponent<ItemDrop>();
 		if ((object)component != null && component.m_itemData.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Consumable && component.IsPiece())
@@ -1206,7 +1206,7 @@
 			m_chestItem = item;
 			if ((bool)m_visEquipment && m_visEquipment.m_isPlayer && !flag)
 			{
-				item.m_shared.m_equipEffect.Create(base.transform.position + Vector3.up, base.transform.rotation, null, 1f, -1, GetZDOID());
+				item.m_shared.m_equipEffect.Create(transform.position + Vector3.up, transform.rotation, null, 1f, -1, GetZDOID());
 			}
 		}
 		else if (item.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Legs)
@@ -1215,7 +1215,7 @@
 			m_legItem = item;
 			if ((bool)m_visEquipment && m_visEquipment.m_isPlayer && !flag)
 			{
-				item.m_shared.m_equipEffect.Create(base.transform.position, base.transform.rotation, null, 1f, -1, GetZDOID());
+				item.m_shared.m_equipEffect.Create(transform.position, transform.rotation, null, 1f, -1, GetZDOID());
 			}
 		}
 		else if (item.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Ammo || item.m_shared.m_itemType == ItemDrop.ItemData.ItemType.AmmoNonEquipable)
@@ -1238,7 +1238,7 @@
 			m_shoulderItem = item;
 			if ((bool)m_visEquipment && m_visEquipment.m_isPlayer && !flag)
 			{
-				item.m_shared.m_equipEffect.Create(base.transform.position + Vector3.up, base.transform.rotation, null, 1f, -1, GetZDOID());
+				item.m_shared.m_equipEffect.Create(transform.position + Vector3.up, transform.rotation, null, 1f, -1, GetZDOID());
 			}
 		}
 		else if (item.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Utility)
@@ -1247,7 +1247,7 @@
 			m_utilityItem = item;
 			if ((bool)m_visEquipment && m_visEquipment.m_isPlayer && !flag)
 			{
-				item.m_shared.m_equipEffect.Create(base.transform.position + Vector3.up, base.transform.rotation, null, 1f, -1, GetZDOID());
+				item.m_shared.m_equipEffect.Create(transform.position + Vector3.up, transform.rotation, null, 1f, -1, GetZDOID());
 			}
 		}
 		else if (item.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Trinket)
@@ -1256,7 +1256,7 @@
 			m_trinketItem = item;
 			if ((bool)m_visEquipment && m_visEquipment.m_isPlayer && !flag)
 			{
-				item.m_shared.m_equipEffect.Create(base.transform.position + Vector3.up, base.transform.rotation, null, 1f, -1, GetZDOID());
+				item.m_shared.m_equipEffect.Create(transform.position + Vector3.up, transform.rotation, null, 1f, -1, GetZDOID());
 			}
 		}
 		if (IsItemEquiped(item))
@@ -1344,7 +1344,7 @@
 		}
 		item.m_equipped = false;
 		SetupEquipment();
-		item.m_shared.m_unequipEffect.Create(base.transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
+		item.m_shared.m_unequipEffect.Create(transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
 		if (triggerEquipEffects)
 		{
 			TriggerEquipEffect(item);
@@ -1356,7 +1356,7 @@
 		if (m_nview.GetZDO() != null && MonoUpdaters.UpdateCount != m_lastEquipEffectFrame)
 		{
 			m_lastEquipEffectFrame = MonoUpdaters.UpdateCount;
-			m_equipEffects.Create(base.transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
+			m_equipEffects.Create(transform.position, Quaternion.identity, null, 1f, -1, GetZDOID());
 		}
 	}
 
@@ -1750,7 +1750,7 @@
 
 	protected override bool BlockAttack(HitData hit, Character attacker)
 	{
-		if (Vector3.Dot(hit.m_dir, base.transform.forward) > 0f)
+		if (Vector3.Dot(hit.m_dir, transform.forward) > 0f)
 		{
 			return false;
 		}
@@ -1769,7 +1769,7 @@
 		}
 		if (currentBlocker.m_shared.m_damageModifiers.Count > 0)
 		{
-			HitData.DamageModifiers modifiers = default(HitData.DamageModifiers);
+			HitData.DamageModifiers modifiers = default;
 			modifiers.Apply(currentBlocker.m_shared.m_damageModifiers);
 			hit.ApplyResistance(modifiers, out var _);
 		}
@@ -1792,9 +1792,9 @@
 		}
 		float totalStaggerDamage = damageTypes.GetTotalStaggerDamage();
 		bool flag2 = AddStaggerDamage(totalStaggerDamage, hit.m_dir, null);
-		bool num4 = HaveStamina();
-		bool flag3 = num4 && !flag2;
-		if (num4 && !flag2)
+		bool flag3 = HaveStamina();
+		bool flag4 = flag3 && !flag2;
+		if (flag3 && !flag2)
 		{
 			hit.m_statusEffectHash = 0;
 			hit.BlockDamage(num);
@@ -1802,8 +1802,8 @@
 		}
 		if (currentBlocker.m_shared.m_useDurability)
 		{
-			float num5 = currentBlocker.m_shared.m_useDurabilityDrain * (totalBlockableDamage / timedBlockBonus);
-			currentBlocker.m_durability -= num5 * Game.m_durabilityRate;
+			float num4 = currentBlocker.m_shared.m_useDurabilityDrain * (totalBlockableDamage / timedBlockBonus);
+			currentBlocker.m_durability -= num4 * Game.m_durabilityRate;
 		}
 		RaiseSkill(Skills.SkillType.Blocking, flag ? 2f : 1f);
 		currentBlocker.m_shared.m_blockEffect.Create(hit.m_point, Quaternion.identity, null, 1f, -1, GetZDOID());
@@ -1811,7 +1811,7 @@
 		{
 			m_blockCharges++;
 			m_blockChargeRemoveTimer = 0f;
-			currentBlocker.m_shared.m_blockChargeEffects.Create(m_visEquipment.m_leftHand.position, base.transform.rotation, null, 1f, m_blockCharges, GetZDOID());
+			currentBlocker.m_shared.m_blockChargeEffects.Create(m_visEquipment.m_leftHand.position, transform.rotation, null, 1f, m_blockCharges, GetZDOID());
 			if (m_blockCharges >= currentBlocker.m_shared.m_maxBlockCharges)
 			{
 				currentBlocker.m_shared.m_attack.StartWithoutAnimation(this, m_body, m_visEquipment, currentBlocker);
@@ -1822,7 +1822,7 @@
 		{
 			AddAdrenaline(currentBlocker.m_shared.m_blockAdrenaline);
 		}
-		if ((bool)attacker & flag & flag3)
+		if ((bool)attacker & flag & flag4)
 		{
 			m_perfectBlockEffect.Create(hit.m_point, Quaternion.identity, null, 1f, -1, GetZDOID());
 			AddAdrenaline(currentBlocker.m_shared.m_perfectBlockAdrenaline);
@@ -1858,15 +1858,15 @@
 				GetSEMan().AddStatusEffect(m_perfectBlockStatusEffect, resetTime: true, currentBlocker.m_worldLevel, GetSkillLevel(Skills.SkillType.Blocking), -1);
 			}
 		}
-		if (flag3)
+		if (flag4)
 		{
 			hit.m_pushForce *= num2;
 			if ((bool)attacker && !hit.m_ranged)
 			{
-				float num6 = 1f - Mathf.Clamp01(num2 * 0.5f);
+				float num5 = 1f - Mathf.Clamp01(num2 * 0.5f);
 				HitData hitData = new HitData();
-				hitData.m_pushForce = currentBlocker.GetDeflectionForce() * num6;
-				hitData.m_dir = attacker.transform.position - base.transform.position;
+				hitData.m_pushForce = currentBlocker.GetDeflectionForce() * num5;
+				hitData.m_dir = attacker.transform.position - transform.position;
 				hitData.m_dir.y = 0f;
 				hitData.m_dir.Normalize();
 				attacker.Damage(hitData);
```
