# `MonsterAI.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+25/-25` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MonsterAI.cs
+++ b/MonsterAI.cs
@@ -242,7 +242,7 @@
 		m_updateTargetTimer -= dt;
 		if (m_updateTargetTimer <= 0f && !m_character.InAttack())
 		{
-			bool flag = Player.IsPlayerInRange(base.transform.position, 50f);
+			bool flag = Player.IsPlayerInRange(transform.position, 50f);
 			m_updateTargetTimer = (flag ? 2f : 6f);
 			Character character = FindEnemy();
 			if ((bool)character)
@@ -331,7 +331,7 @@
 		{
 			m_timeSinceAttacking += dt;
 			float num = 60f;
-			float num2 = Vector3.Distance(m_spawnPoint, base.transform.position);
+			float num2 = Vector3.Distance(m_spawnPoint, transform.position);
 			bool flag5 = HuntPlayer() && (bool)m_targetCreature && m_targetCreature.IsPlayer();
 			if (m_timeSinceSensedTargetCreature > 30f || (!flag5 && (m_timeSinceAttacking > num || (m_maxChaseDistance > 0f && m_timeSinceSensedTargetCreature > 1f && num2 > m_maxChaseDistance))))
 			{
@@ -384,12 +384,12 @@
 				return true;
 			}
 		}
-		if (m_targetCreature is Player player && player.InCrownMode() && m_character.GetFaction() != Character.Faction.Boss && Vector3.Distance(m_targetCreature.transform.position, base.transform.position) - m_targetCreature.GetRadius() < m_crownFearRange)
+		if (m_targetCreature is Player player && player.InCrownMode() && m_character.GetFaction() != Character.Faction.Boss && Vector3.Distance(m_targetCreature.transform.position, transform.position) - m_targetCreature.GetRadius() < m_crownFearRange)
 		{
 			Flee(dt, m_targetCreature.transform.position);
 			return true;
 		}
-		if (m_fleeIfNotAlerted && !HuntPlayer() && (bool)m_targetCreature && !IsAlerted() && Vector3.Distance(m_targetCreature.transform.position, base.transform.position) - m_targetCreature.GetRadius() > m_alertRange)
+		if (m_fleeIfNotAlerted && !HuntPlayer() && (bool)m_targetCreature && !IsAlerted() && Vector3.Distance(m_targetCreature.transform.position, transform.position) - m_targetCreature.GetRadius() > m_alertRange)
 		{
 			Flee(dt, m_targetCreature.transform.position);
 			return true;
@@ -425,7 +425,7 @@
 			}
 			else
 			{
-				EffectArea effectArea = EffectArea.IsPointCloseToNoMonsterArea(base.transform.position);
+				EffectArea effectArea = EffectArea.IsPointCloseToNoMonsterArea(transform.position);
 				if (effectArea != null)
 				{
 					Flee(dt, effectArea.transform.position);
@@ -436,7 +436,7 @@
 		if (m_fleeIfHurtWhenTargetCantBeReached && m_targetCreature != null && m_timeSinceAttacking > 30f && m_timeSinceHurt < 20f)
 		{
 			Flee(dt, m_targetCreature.transform.position);
-			m_lastKnownTargetPos = base.transform.position;
+			m_lastKnownTargetPos = transform.position;
 			m_updateTargetTimer = 1f;
 			return true;
 		}
@@ -496,8 +496,8 @@
 		{
 			if ((bool)m_targetStatic)
 			{
-				Vector3 vector = m_targetStatic.FindClosestPoint(base.transform.position);
-				if (Vector3.Distance(vector, base.transform.position) < itemData.m_shared.m_aiAttackRange && CanSeeTarget(m_targetStatic))
+				Vector3 vector = m_targetStatic.FindClosestPoint(transform.position);
+				if (Vector3.Distance(vector, transform.position) < itemData.m_shared.m_aiAttackRange && CanSeeTarget(m_targetStatic))
 				{
 					LookAt(m_targetStatic.GetCenter());
 					if (itemData.m_shared.m_aiAttackMaxAngle == 0f)
@@ -525,14 +525,14 @@
 				{
 					m_beenAtLastPos = false;
 					m_lastKnownTargetPos = m_targetCreature.transform.position;
-					float num = Vector3.Distance(m_lastKnownTargetPos, base.transform.position) - m_targetCreature.GetRadius();
+					float num = Vector3.Distance(m_lastKnownTargetPos, transform.position) - m_targetCreature.GetRadius();
 					float num2 = m_alertRange * m_targetCreature.GetStealthFactor();
 					if (canSeeTarget && num < num2)
 					{
 						SetAlerted(alert: true);
 					}
-					bool num3 = num < itemData.m_shared.m_aiAttackRange;
-					if (!num3 || !canSeeTarget || itemData.m_shared.m_aiAttackRangeMin < 0f || !IsAlerted())
+					bool flag4 = num < itemData.m_shared.m_aiAttackRange;
+					if (!flag4 || !canSeeTarget || itemData.m_shared.m_aiAttackRangeMin < 0f || !IsAlerted())
 					{
 						Vector3 velocity = m_targetCreature.GetVelocity();
 						Vector3 vector2 = velocity * m_interceptTime;
@@ -551,7 +551,7 @@
 					{
 						StopMoving();
 					}
-					if ((num3 & canSeeTarget) && IsAlerted())
+					if ((flag4 & canSeeTarget) && IsAlerted())
 					{
 						if (PheromoneFleeCheck(m_targetCreature))
 						{
@@ -592,7 +592,7 @@
 			Character character = ((itemData.m_shared.m_aiTargetType == ItemDrop.ItemData.AiTarget.FriendHurt) ? HaveHurtFriendInRange(m_viewRange) : HaveFriendInRange(m_viewRange));
 			if ((bool)character)
 			{
-				if (Vector3.Distance(character.transform.position, base.transform.position) < itemData.m_shared.m_aiAttackRange)
+				if (Vector3.Distance(character.transform.position, transform.position) < itemData.m_shared.m_aiAttackRange)
 				{
 					if (flag3)
 					{
@@ -612,7 +612,7 @@
 			}
 			else
 			{
-				RandomMovement(dt, base.transform.position, snapToGround: true);
+				RandomMovement(dt, transform.position, snapToGround: true);
 			}
 		}
 		return true;
@@ -664,7 +664,7 @@
 					{
 						m_onConsumedItem(m_consumeTarget);
 					}
-					humanoid.m_consumeItemEffects.Create(base.transform.position, Quaternion.identity);
+					humanoid.m_consumeItemEffects.Create(transform.position, Quaternion.identity);
 					m_animator.SetTrigger("consume");
 					m_consumeTarget = null;
 				}
@@ -680,7 +680,7 @@
 		{
 			m_itemMask = LayerMask.GetMask("item");
 		}
-		Collider[] array = Physics.OverlapSphere(base.transform.position, maxRange, m_itemMask);
+		Collider[] array = Physics.OverlapSphere(transform.position, maxRange, m_itemMask);
 		ItemDrop itemDrop = null;
 		float num = 999999f;
 		Collider[] array2 = array;
@@ -693,7 +693,7 @@
 			ItemDrop component = collider.attachedRigidbody.GetComponent<ItemDrop>();
 			if (!(component == null) && component.GetComponent<ZNetView>().IsValid() && CanConsume(component.m_itemData))
 			{
-				float num2 = Vector3.Distance(component.transform.position, base.transform.position);
+				float num2 = Vector3.Distance(component.transform.position, transform.position);
 				if (itemDrop == null || num2 < num)
 				{
 					itemDrop = component;
@@ -746,12 +746,12 @@
 		{
 			return false;
 		}
-		bool num = m_character.StartAttack(target, charge: false);
-		if (num)
+		bool flag = m_character.StartAttack(target, charge: false);
+		if (flag)
 		{
 			m_timeSinceAttacking = 0f;
 		}
-		return num;
+		return flag;
 	}
 
 	public void SetDespawnInDay(bool despawn)
@@ -819,7 +819,7 @@
 		Player player = null;
 		if (m_wakeupRange > 0f || m_fallAsleepDistance > 0f)
 		{
-			player = Player.GetClosestPlayer(base.transform.position, m_wakeupRange);
+			player = Player.GetClosestPlayer(transform.position, m_wakeupRange);
 			if (player != null && (player.InGhostMode() || player.IsDebugFlying()))
 			{
 				player = null;
@@ -827,7 +827,7 @@
 		}
 		if (!IsSleeping())
 		{
-			if (m_fallAsleepDistance > 0f && (player == null || Vector3.Distance(player.transform.position, base.transform.position) > m_fallAsleepDistance))
+			if (m_fallAsleepDistance > 0f && (player == null || Vector3.Distance(player.transform.position, transform.position) > m_fallAsleepDistance))
 			{
 				Sleep();
 			}
@@ -848,7 +848,7 @@
 		}
 		else if (m_noiseWakeup)
 		{
-			Player playerNoiseRange = Player.GetPlayerNoiseRange(base.transform.position, m_maxNoiseWakeupRange);
+			Player playerNoiseRange = Player.GetPlayerNoiseRange(transform.position, m_maxNoiseWakeupRange);
 			if ((bool)playerNoiseRange && !playerNoiseRange.InGhostMode() && !playerNoiseRange.IsDebugFlying())
 			{
 				Wakeup();
@@ -882,7 +882,7 @@
 		{
 			m_animator.SetBool(s_sleeping, value: false);
 			m_nview.GetZDO().Set(ZDOVars.s_sleeping, value: false);
-			m_wakeupEffects.Create(base.transform.position, base.transform.rotation);
+			m_wakeupEffects.Create(transform.position, transform.rotation);
 			m_sleeping = false;
 			m_nview.InvokeRPC(ZNetView.Everybody, "RPC_Wakeup");
 		}
@@ -905,7 +905,7 @@
 			m_targetCreature = null;
 			m_animator.SetBool(s_sleeping, value: true);
 			m_nview.GetZDO().Set(ZDOVars.s_sleeping, value: true);
-			m_sleepEffects.Create(base.transform.position, base.transform.rotation);
+			m_sleepEffects.Create(transform.position, transform.rotation);
 			m_sleeping = true;
 			m_nview.InvokeRPC(ZNetView.Everybody, "RPC_Sleep");
 		}
```
