# `Attack.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+22/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Attack.cs
+++ b/Attack.cs
@@ -520,8 +520,8 @@
 			return;
 		}
 		m_time += dt;
-		bool num = m_character.InAttack();
-		if (num)
+		bool flag = m_character.InAttack();
+		if (flag)
 		{
 			if (m_character.IsStaggering())
 			{
@@ -553,7 +553,7 @@
 			}
 		}
 		UpdateProjectile(dt);
-		if ((!num && m_wasInAttack) || m_abortAttack)
+		if ((!flag && m_wasInAttack) || m_abortAttack)
 		{
 			Stop();
 		}
@@ -758,12 +758,12 @@
 			}
 			if (ammoItem.m_shared.m_itemType == ItemDrop.ItemData.ItemType.Consumable)
 			{
-				bool num = m_character.ConsumeItem(m_character.GetInventory(), ammoItem);
-				if (num)
+				bool flag = m_character.ConsumeItem(m_character.GetInventory(), ammoItem);
+				if (flag)
 				{
 					m_ammoItem = ammoItem;
 				}
-				return num;
+				return flag;
 			}
 			m_character.GetInventory().RemoveItem(ammoItem, 1);
 			m_ammoItem = ammoItem;
@@ -1184,7 +1184,7 @@
 								Terminal.Log($"{m_character} AOE attacking {gameObject} for {hitData}");
 							}
 							component.Damage(hitData);
-							if ((component.GetDestructibleType() & m_skillHitType) != DestructibleType.None)
+							if ((component.GetDestructibleType() & m_skillHitType) != 0)
 							{
 								raiseSkill = true;
 							}
@@ -1376,12 +1376,12 @@
 			{
 				DestructibleType destructibleType = component3.GetDestructibleType();
 				Skills.SkillType skillType = m_weapon.m_shared.m_skillType;
-				if (m_specialHitSkill != Skills.SkillType.None && (destructibleType & m_specialHitType) != DestructibleType.None)
+				if (m_specialHitSkill != Skills.SkillType.None && (destructibleType & m_specialHitType) != 0)
 				{
 					skillType = m_specialHitSkill;
 					hashSet.Add(m_specialHitSkill);
 				}
-				else if ((destructibleType & m_skillHitType) != DestructibleType.None)
+				else if ((destructibleType & m_skillHitType) != 0)
 				{
 					hashSet.Add(skillType);
 				}
@@ -1437,7 +1437,7 @@
 				{
 					m_character.AddEitr(m_attackEitrAdd);
 				}
-				if ((destructibleType & m_resetChainIfHit) != DestructibleType.None)
+				if ((destructibleType & m_resetChainIfHit) != 0)
 				{
 					m_nextAttackChainLevel = 0;
 				}
@@ -1710,7 +1710,18 @@
 			}
 		}
 		TerrainModifier.SetTriggerOnPlaced(trigger: true);
-		GameObject gameObject = UnityEngine.Object.Instantiate(prefab, hitPoint, randomRotation ? Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) : ((character != null) ? Quaternion.LookRotation(character.transform.forward) : Quaternion.identity));
+		GameObject original = prefab;
+		Vector3 position = hitPoint;
+		Quaternion rotation;
+		if (randomRotation)
+		{
+			rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
+		}
+		else
+		{
+			rotation = ((character != null) ? Quaternion.LookRotation(character.transform.forward) : Quaternion.identity);
+		}
+		GameObject gameObject = UnityEngine.Object.Instantiate(original, position, rotation);
 		TerrainModifier.SetTriggerOnPlaced(trigger: false);
 		gameObject.GetComponent<IProjectile>()?.Setup(character, Vector3.zero, attackHitNoise, null, weapon, ammo);
 		return gameObject;
```
