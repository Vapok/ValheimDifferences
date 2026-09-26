# `BaseAI.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+65/-65` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/BaseAI.cs
+++ b/BaseAI.cs
@@ -242,7 +242,7 @@
 		if (zDO != null)
 		{
 			m_huntPlayer = zDO.GetBool(ZDOVars.s_huntPlayer, m_huntPlayer);
-			m_spawnPoint = zDO.GetVec3(ZDOVars.s_spawnPoint, base.transform.position);
+			m_spawnPoint = zDO.GetVec3(ZDOVars.s_spawnPoint, transform.position);
 			if (m_nview.IsOwner())
 			{
 				zDO.Set(ZDOVars.s_spawnPoint, m_spawnPoint);
@@ -270,7 +270,7 @@
 
 	public void SetPatrolPoint()
 	{
-		SetPatrolPoint(base.transform.position);
+		SetPatrolPoint(transform.position);
 	}
 
 	private void SetPatrolPoint(Vector3 point)
@@ -418,13 +418,13 @@
 	{
 		if (!IsSleeping() && !(UnityEngine.Random.value > m_idleSoundChance))
 		{
-			m_idleSound.Create(base.transform.position, Quaternion.identity);
+			m_idleSound.Create(transform.position, Quaternion.identity);
 		}
 	}
 
 	protected void Follow(GameObject go, float dt)
 	{
-		float num = Vector3.Distance(go.transform.position, base.transform.position);
+		float num = Vector3.Distance(go.transform.position, transform.position);
 		bool run = num > 10f;
 		if (num < 3f)
 		{
@@ -442,11 +442,11 @@
 		if (Time.time - m_lastMoveToWaterUpdate > num)
 		{
 			m_lastMoveToWaterUpdate = Time.time;
-			Vector3 moveToWaterPosition = base.transform.position;
+			Vector3 moveToWaterPosition = transform.position;
 			for (int i = 0; i < 10; i++)
 			{
 				Vector3 vector = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * UnityEngine.Random.Range(4f, maxRange);
-				Vector3 vector2 = base.transform.position + vector;
+				Vector3 vector2 = transform.position + vector;
 				vector2.y = ZoneSystem.instance.GetSolidHeight(vector2);
 				if (vector2.y < moveToWaterPosition.y)
 				{
@@ -465,17 +465,17 @@
 		}
 		if (m_haveWaterPosition)
 		{
-			MoveTowards(m_moveToWaterPosition - base.transform.position, run: true);
+			MoveTowards(m_moveToWaterPosition - transform.position, run: true);
 		}
 	}
 
 	protected void MoveAwayAndDespawn(float dt, bool run)
 	{
-		Player closestPlayer = Player.GetClosestPlayer(base.transform.position, 40f);
+		Player closestPlayer = Player.GetClosestPlayer(transform.position, 40f);
 		if (closestPlayer != null)
 		{
-			Vector3 normalized = (closestPlayer.transform.position - base.transform.position).normalized;
-			MoveTo(dt, base.transform.position - normalized * 5f, 0f, run);
+			Vector3 normalized = (closestPlayer.transform.position - transform.position).normalized;
+			MoveTo(dt, transform.position - normalized * 5f, 0f, run);
 		}
 		else
 		{
@@ -485,7 +485,7 @@
 
 	protected void IdleMovement(float dt)
 	{
-		Vector3 centerPoint = ((m_character.IsTamed() || HuntPlayer()) ? base.transform.position : m_spawnPoint);
+		Vector3 centerPoint = ((m_character.IsTamed() || HuntPlayer()) ? transform.position : m_spawnPoint);
 		if (GetPatrolPoint(out var point))
 		{
 			centerPoint = point;
@@ -501,17 +501,17 @@
 			{
 				centerPoint.y = height;
 			}
-			if (Utils.DistanceXZ(centerPoint, base.transform.position) > m_randomMoveRange * 2f)
-			{
-				Vector3 vector = centerPoint - base.transform.position;
+			if (Utils.DistanceXZ(centerPoint, transform.position) > m_randomMoveRange * 2f)
+			{
+				Vector3 vector = centerPoint - transform.position;
 				vector.y = 0f;
 				vector.Normalize();
 				vector = Quaternion.Euler(0f, UnityEngine.Random.Range(-30, 30), 0f) * vector;
-				m_randomMoveTarget = base.transform.position + vector * m_randomMoveRange * 2f;
+				m_randomMoveTarget = transform.position + vector * m_randomMoveRange * 2f;
 			}
 			else
 			{
-				Vector3 vector2 = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * base.transform.forward * UnityEngine.Random.Range(m_randomMoveRange * 0.7f, m_randomMoveRange);
+				Vector3 vector2 = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * transform.forward * UnityEngine.Random.Range(m_randomMoveRange * 0.7f, m_randomMoveRange);
 				m_randomMoveTarget = centerPoint + vector2;
 			}
 			if (m_character.IsFlying())
@@ -531,7 +531,7 @@
 		}
 		if (!m_reachedRandomMoveTarget)
 		{
-			bool flag = IsAlerted() || Utils.DistanceXZ(base.transform.position, centerPoint) > m_randomMoveRange * 2f;
+			bool flag = IsAlerted() || Utils.DistanceXZ(transform.position, centerPoint) > m_randomMoveRange * 2f;
 			if (MoveTo(dt, m_randomMoveTarget, 0f, flag))
 			{
 				m_reachedRandomMoveTarget = true;
@@ -560,13 +560,13 @@
 		{
 			m_lastFlee = time;
 			m_fleeTargetUpdateTime = time;
-			Vector3 vector = -(from - base.transform.position);
+			Vector3 vector = -(from - transform.position);
 			vector.y = 0f;
 			vector.Normalize();
 			bool flag = false;
 			for (int i = 0; i < 10; i++)
 			{
-				m_fleeTarget = base.transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0f - m_fleeAngle, m_fleeAngle), 0f) * vector * m_fleeRange;
+				m_fleeTarget = transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0f - m_fleeAngle, m_fleeAngle), 0f) * vector * m_fleeRange;
 				if (HavePath(m_fleeTarget) && (!m_avoidWater || m_character.IsSwimming() || !(ZoneSystem.instance.GetSolidHeight(m_fleeTarget) < 30f)) && (!m_avoidLavaFlee || !ZoneSystem.instance.IsLava(m_fleeTarget)))
 				{
 					flag = true;
@@ -575,7 +575,7 @@
 			}
 			if (!flag)
 			{
-				m_fleeTarget = base.transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * m_fleeRange;
+				m_fleeTarget = transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * m_fleeRange;
 			}
 		}
 		return MoveTo(dt, m_fleeTarget, 1f, IsAlerted());
@@ -589,7 +589,7 @@
 		}
 		if (superAfraid)
 		{
-			EffectArea effectArea = EffectArea.IsPointInsideArea(base.transform.position, EffectArea.Type.Fire, 3f);
+			EffectArea effectArea = EffectArea.IsPointInsideArea(transform.position, EffectArea.Type.Fire, 3f);
 			if ((bool)effectArea)
 			{
 				m_nearFireTime = Time.time;
@@ -604,7 +604,7 @@
 		}
 		else
 		{
-			EffectArea effectArea2 = EffectArea.IsPointInsideArea(base.transform.position, EffectArea.Type.Fire, 3f);
+			EffectArea effectArea2 = EffectArea.IsPointInsideArea(transform.position, EffectArea.Type.Fire, 3f);
 			if ((bool)effectArea2)
 			{
 				if (moveToTarget != null && (bool)EffectArea.IsPointInsideArea(moveToTarget.transform.position, EffectArea.Type.Fire))
@@ -626,17 +626,17 @@
 		if (time - aroundPointUpdateTime > m_randomCircleInterval)
 		{
 			aroundPointUpdateTime = time;
-			Vector3 vector = base.transform.position - point;
+			Vector3 vector = transform.position - point;
 			vector.y = 0f;
 			vector.Normalize();
-			float num = ((!(Vector3.Distance(base.transform.position, point) < distance / 2f)) ? ((float)(((double)UnityEngine.Random.value > 0.5) ? 40 : (-40))) : ((float)(((double)UnityEngine.Random.value > 0.5) ? 90 : (-90))));
+			float num = ((!(Vector3.Distance(transform.position, point) < distance / 2f)) ? ((float)(((double)UnityEngine.Random.value > 0.5) ? 40 : (-40))) : ((float)(((double)UnityEngine.Random.value > 0.5) ? 90 : (-90))));
 			Vector3 vector2 = Quaternion.Euler(0f, num, 0f) * vector;
 			arroundPointTarget = point + vector2 * distance;
-			if (Vector3.Dot(base.transform.forward, arroundPointTarget - base.transform.position) < 0f)
+			if (Vector3.Dot(transform.forward, arroundPointTarget - transform.position) < 0f)
 			{
 				vector2 = Quaternion.Euler(0f, 0f - num, 0f) * vector;
 				arroundPointTarget = point + vector2 * distance;
-				if (m_serpentMovement && Vector3.Distance(point, base.transform.position) > distance / 2f && Vector3.Dot(base.transform.forward, arroundPointTarget - base.transform.position) < 0f)
+				if (m_serpentMovement && Vector3.Distance(point, transform.position) > distance / 2f && Vector3.Dot(transform.forward, arroundPointTarget - transform.position) < 0f)
 				{
 					arroundPointTarget = point - vector2 * distance;
 				}
@@ -680,7 +680,7 @@
 		{
 			if (m_character.IsSwimming())
 			{
-				if (GetSolidHeight(base.transform.position, 20f, 100f, out var height2) && height < height2)
+				if (GetSolidHeight(transform.position, 20f, 100f, out var height2) && height < height2)
 				{
 					return false;
 				}
@@ -721,7 +721,7 @@
 
 	public bool CanSenseTarget(Character target, bool passiveAggresive)
 	{
-		return CanSenseTarget(base.transform, m_character.m_eye.position, m_hearRange, m_viewRange, m_viewAngle, IsAlerted(), m_mistVision, target, passiveAggresive, m_character.IsTamed());
+		return CanSenseTarget(transform, m_character.m_eye.position, m_hearRange, m_viewRange, m_viewAngle, IsAlerted(), m_mistVision, target, passiveAggresive, m_character.IsTamed());
 	}
 
 	public static bool CanSenseTarget(Transform me, Vector3 eyePoint, float hearRange, float viewRange, float viewAngle, bool alerted, bool mistVision, Character target, bool passiveAggresive, bool isTamed)
@@ -743,7 +743,7 @@
 
 	public bool CanHearTarget(Character target)
 	{
-		return CanHearTarget(base.transform, m_hearRange, target);
+		return CanHearTarget(transform, m_hearRange, target);
 	}
 
 	public static bool CanHearTarget(Transform me, float hearRange, Character target)
@@ -774,7 +774,7 @@
 
 	public bool CanSeeTarget(Character target)
 	{
-		return CanSeeTarget(base.transform, m_character.m_eye.position, m_viewRange, m_viewAngle, IsAlerted(), m_mistVision, target);
+		return CanSeeTarget(transform, m_character.m_eye.position, m_viewRange, m_viewAngle, IsAlerted(), m_mistVision, target);
 	}
 
 	public static bool CanSeeTarget(Transform me, Vector3 eyePoint, float viewRange, float viewAngle, bool alerted, bool mistVision, Character target)
@@ -827,12 +827,12 @@
 			return false;
 		}
 		Vector3 center = target.GetCenter();
-		if (Vector3.Distance(center, base.transform.position) > m_viewRange)
+		if (Vector3.Distance(center, transform.position) > m_viewRange)
 		{
 			return false;
 		}
 		Vector3 rhs = center - m_character.m_eye.position;
-		if (m_viewRange > 0f && !IsAlerted() && Vector3.Dot(base.transform.forward, rhs) < 0f)
+		if (m_viewRange > 0f && !IsAlerted() && Vector3.Dot(transform.forward, rhs) < 0f)
 		{
 			return false;
 		}
@@ -861,7 +861,7 @@
 		float num2 = Mathf.Clamp01(distance / m_serpentTurnRadius);
 		float num3 = 1f - (1f - num2) * (1f - num);
 		num3 = num3 * 0.9f + 0.1f;
-		Vector3 moveDir = base.transform.forward * num3;
+		Vector3 moveDir = transform.forward * num3;
 		LookTowards(dir);
 		m_character.SetMoveDir(moveDir);
 		m_character.SetRun(run);
@@ -873,9 +873,9 @@
 		LookTowards(dir);
 		if (m_smoothMovement)
 		{
-			float num = Vector3.Angle(new Vector3(dir.x, 0f, dir.z), base.transform.forward);
+			float num = Vector3.Angle(new Vector3(dir.x, 0f, dir.z), transform.forward);
 			float num2 = 1f - Mathf.Clamp01(num / m_moveMinAngle);
-			Vector3 moveDir = base.transform.forward * num2;
+			Vector3 moveDir = transform.forward * num2;
 			moveDir.y = dir.y;
 			m_character.SetMoveDir(moveDir);
 			m_character.SetRun(run);
@@ -918,13 +918,13 @@
 
 	public bool IsLookingAt(Vector3 point, float minAngle, bool inverted = false)
 	{
-		return IsLookingTowards((point - base.transform.position).normalized, minAngle) ^ inverted;
+		return IsLookingTowards((point - transform.position).normalized, minAngle) ^ inverted;
 	}
 
 	public bool IsLookingTowards(Vector3 dir, float minAngle)
 	{
 		dir.y = 0f;
-		Vector3 forward = base.transform.forward;
+		Vector3 forward = transform.forward;
 		forward.y = 0f;
 		return Vector3.Angle(dir, forward) < minAngle;
 	}
@@ -940,7 +940,7 @@
 		{
 			return true;
 		}
-		return Pathfinding.instance.HavePath(base.transform.position, target, m_pathAgentType);
+		return Pathfinding.instance.HavePath(transform.position, target, m_pathAgentType);
 	}
 
 	protected bool FindPath(Vector3 target)
@@ -957,7 +957,7 @@
 		}
 		m_lastFindPathTarget = target;
 		m_lastFindPathTime = time;
-		m_lastFindPathResult = Pathfinding.instance.GetPath(base.transform.position, target, m_path, m_pathAgentType);
+		m_lastFindPathResult = Pathfinding.instance.GetPath(transform.position, target, m_path, m_pathAgentType);
 		return m_lastFindPathResult;
 	}
 
@@ -982,7 +982,7 @@
 		{
 			num = 3f;
 		}
-		if (Utils.DistanceXZ(point, base.transform.position) < Mathf.Max(dist, num))
+		if (Utils.DistanceXZ(point, transform.position) < Mathf.Max(dist, num))
 		{
 			StopMoving();
 			return true;
@@ -998,7 +998,7 @@
 			return true;
 		}
 		Vector3 vector = m_path[0];
-		if (Utils.DistanceXZ(vector, base.transform.position) < num)
+		if (Utils.DistanceXZ(vector, transform.position) < num)
 		{
 			m_path.RemoveAt(0);
 			if (m_path.Count == 0)
@@ -1009,13 +1009,13 @@
 		}
 		else if (m_serpentMovement)
 		{
-			float distance = Vector3.Distance(vector, base.transform.position);
-			Vector3 normalized = (vector - base.transform.position).normalized;
+			float distance = Vector3.Distance(vector, transform.position);
+			Vector3 normalized = (vector - transform.position).normalized;
 			MoveTowardsSwoop(normalized, run, distance);
 		}
 		else
 		{
-			Vector3 normalized2 = (vector - base.transform.position).normalized;
+			Vector3 normalized2 = (vector - transform.position).normalized;
 			MoveTowards(normalized2, run);
 		}
 		return false;
@@ -1023,7 +1023,7 @@
 
 	protected bool MoveAndAvoid(float dt, Vector3 point, float dist, bool run)
 	{
-		Vector3 vector = point - base.transform.position;
+		Vector3 vector = point - transform.position;
 		if (m_character.IsFlying())
 		{
 			if (vector.magnitude < dist)
@@ -1056,7 +1056,7 @@
 			m_stuckTimer += Time.fixedDeltaTime;
 			if (m_stuckTimer > 1.5f)
 			{
-				if (Vector3.Distance(base.transform.position, m_lastPosition) < 0.2f)
+				if (Vector3.Distance(transform.position, m_lastPosition) < 0.2f)
 				{
 					m_getOutOfCornerTimer = 4f;
 					m_getOutOfCornerAngle = UnityEngine.Random.Range(-20f, 20f);
@@ -1064,7 +1064,7 @@
 					return false;
 				}
 				m_stuckTimer = 0f;
-				m_lastPosition = base.transform.position;
+				m_lastPosition = transform.position;
 			}
 		}
 		if (CanMove(vector, radius, num))
@@ -1073,13 +1073,13 @@
 		}
 		else
 		{
-			Vector3 forward = base.transform.forward;
+			Vector3 forward = transform.forward;
 			if (m_character.IsFlying())
 			{
 				forward.y = 0.2f;
 				forward.Normalize();
 			}
-			Vector3 vector2 = base.transform.right * radius * 0.75f;
+			Vector3 vector2 = transform.right * radius * 0.75f;
 			float num2 = num * 1.5f;
 			Vector3 centerPoint = m_character.GetCenterPoint();
 			float num3 = Raycast(centerPoint - vector2, forward, num2, 0.1f);
@@ -1108,7 +1108,7 @@
 	private bool CanMove(Vector3 dir, float checkRadius, float distance)
 	{
 		Vector3 centerPoint = m_character.GetCenterPoint();
-		Vector3 right = base.transform.right;
+		Vector3 right = transform.right;
 		if (Raycast(centerPoint, dir, distance, 0.1f) < distance)
 		{
 			return false;
@@ -1292,7 +1292,7 @@
 	protected StaticTarget FindRandomStaticTarget(float maxDistance)
 	{
 		float radius = m_character.GetRadius();
-		int num = Physics.OverlapSphereNonAlloc(base.transform.position, radius + maxDistance, s_tempSphereOverlap);
+		int num = Physics.OverlapSphereNonAlloc(transform.position, radius + maxDistance, s_tempSphereOverlap);
 		if (num == 0)
 		{
 			return null;
@@ -1316,7 +1316,7 @@
 	protected StaticTarget FindClosestStaticPriorityTarget()
 	{
 		float num = ((m_viewRange > 0f) ? m_viewRange : m_hearRange);
-		int num2 = Physics.OverlapSphereNonAlloc(base.transform.position, num, s_tempSphereOverlap, m_monsterTargetRayMask);
+		int num2 = Physics.OverlapSphereNonAlloc(transform.position, num, s_tempSphereOverlap, m_monsterTargetRayMask);
 		if (num2 == 0)
 		{
 			return null;
@@ -1328,7 +1328,7 @@
 			StaticTarget componentInParent = s_tempSphereOverlap[i].GetComponentInParent<StaticTarget>();
 			if (!(componentInParent == null) && componentInParent.IsPriorityTarget())
 			{
-				float num4 = Vector3.Distance(base.transform.position, componentInParent.GetCenter());
+				float num4 = Vector3.Distance(transform.position, componentInParent.GetCenter());
 				if (num4 < num3 && CanSeeTarget(componentInParent))
 				{
 					result = componentInParent;
@@ -1350,7 +1350,7 @@
 	{
 		foreach (Character character in characters)
 		{
-			if (!(character == m_character) && !IsEnemy(m_character, character) && !(Vector3.Distance(character.transform.position, base.transform.position) > range))
+			if (!(character == m_character) && !IsEnemy(m_character, character) && !(Vector3.Distance(character.transform.position, transform.position) > range))
 			{
 				return character;
 			}
@@ -1368,7 +1368,7 @@
 	{
 		foreach (Character character in characters)
 		{
-			if (!IsEnemy(m_character, character) && !(Vector3.Distance(character.transform.position, base.transform.position) > range) && character.GetHealth() < character.GetMaxHealth())
+			if (!IsEnemy(m_character, character) && !(Vector3.Distance(character.transform.position, transform.position) > range) && character.GetHealth() < character.GetMaxHealth())
 			{
 				return character;
 			}
@@ -1378,9 +1378,9 @@
 
 	protected float StandStillDuration(float distanceTreshold)
 	{
-		if (Vector3.Distance(base.transform.position, m_lastMovementCheck) > distanceTreshold)
-		{
-			m_lastMovementCheck = base.transform.position;
+		if (Vector3.Distance(transform.position, m_lastMovementCheck) > distanceTreshold)
+		{
+			m_lastMovementCheck = transform.position;
 			m_lastMoveTime = Time.time;
 		}
 		return Time.time - m_lastMoveTime;
@@ -1406,7 +1406,7 @@
 			BaseAI baseAI = item.GetBaseAI();
 			if ((!(baseAI != null) || !baseAI.IsSleeping()) && CanSenseTarget(item))
 			{
-				float num2 = Vector3.Distance(item.transform.position, base.transform.position);
+				float num2 = Vector3.Distance(item.transform.position, transform.position);
 				if (num2 < num || character == null)
 				{
 					character = item;
@@ -1416,7 +1416,7 @@
 		}
 		if (character == null && HuntPlayer())
 		{
-			Player closestPlayer = Player.GetClosestPlayer(base.transform.position, 200f);
+			Player closestPlayer = Player.GetClosestPlayer(transform.position, 200f);
 			if ((bool)closestPlayer && (closestPlayer.InDebugFlyMode() || closestPlayer.InGhostMode()))
 			{
 				return null;
@@ -1501,7 +1501,7 @@
 	{
 		foreach (BaseAI instance in m_instances)
 		{
-			if (Vector3.Distance(base.transform.position, instance.transform.position) < range && instance.IsAlerted())
+			if (Vector3.Distance(transform.position, instance.transform.position) < range && instance.IsAlerted())
 			{
 				return true;
 			}
@@ -1563,7 +1563,7 @@
 			}
 			if (m_alerted)
 			{
-				m_alertedEffects.Create(base.transform.position, Quaternion.identity);
+				m_alertedEffects.Create(transform.position, Quaternion.identity);
 			}
 			if (m_character.IsBoss() && !m_nview.GetZDO().GetBool(ZDOVars.s_bossCount))
 			{
@@ -1670,7 +1670,7 @@
 
 	private float GetAltitude()
 	{
-		if (Physics.Raycast(base.transform.position, Vector3.down, out var hitInfo, m_solidRayMask))
+		if (Physics.Raycast(transform.position, Vector3.down, out var hitInfo, m_solidRayMask))
 		{
 			return m_character.transform.position.y - hitInfo.point.y;
 		}
@@ -1698,13 +1698,13 @@
 				Gizmos.DrawSphere(item + Vector3.up * 0.1f, 0.1f);
 			}
 			Gizmos.color = Color.green;
-			Gizmos.DrawLine(base.transform.position, m_lastFindPathTarget);
+			Gizmos.DrawLine(transform.position, m_lastFindPathTarget);
 			Gizmos.DrawSphere(m_lastFindPathTarget, 0.2f);
 		}
 		else
 		{
 			Gizmos.color = Color.red;
-			Gizmos.DrawLine(base.transform.position, m_lastFindPathTarget);
+			Gizmos.DrawLine(transform.position, m_lastFindPathTarget);
 			Gizmos.DrawSphere(m_lastFindPathTarget, 0.2f);
 		}
 	}
```
