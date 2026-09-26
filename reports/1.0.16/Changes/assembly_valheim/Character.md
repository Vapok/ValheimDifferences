# `Character.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+129/-114` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Character.cs
+++ b/Character.cs
@@ -768,7 +768,7 @@
 	{
 		if (m_killedForAchievements == Utils.AchievementInclusion.Undefined)
 		{
-			ZLog.LogError("The mob " + base.name + " had an AchievementInclusion property of \"" + Utils.AchievementInclusion.Undefined.ToString() + "\" on the BaseAI component - Set it to \"" + Utils.AchievementInclusion.Included.ToString() + "\" if this enemy should be " + $"tracked for achievement stats, and \"{Utils.AchievementInclusion.Excluded}\" otherwise.");
+			ZLog.LogError("The mob " + name + " had an AchievementInclusion property of \"" + Utils.AchievementInclusion.Undefined.ToString() + "\" on the BaseAI component - Set it to \"" + Utils.AchievementInclusion.Included.ToString() + "\" if this enemy should be " + $"tracked for achievement stats, and \"{Utils.AchievementInclusion.Excluded}\" otherwise.");
 		}
 	}
 
@@ -813,7 +813,7 @@
 			return;
 		}
 		ZDO zDO = m_nview.GetZDO();
-		bool num = zDO.IsOwner();
+		bool flag = zDO.IsOwner();
 		bool visible = zDO.HasOwner();
 		CalculateLiquidDepth();
 		UpdateLayer();
@@ -823,7 +823,7 @@
 		SetVisible(visible);
 		UpdateLookTransition(dt);
 		m_hitWorldTime += dt;
-		if (num)
+		if (flag)
 		{
 			UpdateGroundContact(dt);
 			UpdateNoise(dt);
@@ -847,7 +847,7 @@
 		UpdateHeatEffects(dt);
 		if (IsPlayer() && Terminal.m_showTests)
 		{
-			Terminal.m_testList["Player.Zone"] = ZoneSystem.GetZone(base.transform.position).ToString();
+			Terminal.m_testList["Player.Zone"] = ZoneSystem.GetZone(transform.position).ToString();
 		}
 	}
 
@@ -889,12 +889,12 @@
 		if (m_underWorldCheckTimer > 5f || IsPlayer())
 		{
 			m_underWorldCheckTimer = 0f;
-			float groundHeight = ZoneSystem.instance.GetGroundHeight(base.transform.position);
-			if (base.transform.position.y < groundHeight - 1f)
-			{
-				Vector3 position = base.transform.position;
+			float groundHeight = ZoneSystem.instance.GetGroundHeight(transform.position);
+			if (transform.position.y < groundHeight - 1f)
+			{
+				Vector3 position = transform.position;
 				position.y = groundHeight + 0.5f;
-				base.transform.position = position;
+				transform.position = position;
 				m_body.position = position;
 				m_body.linearVelocity = Vector3.zero;
 			}
@@ -919,7 +919,7 @@
 			{
 				if (statusEffect is SE_Stats sE_Stats && sE_Stats.m_pheromoneTarget != null && sE_Stats.m_pheromoneTarget.GetComponent<Character>().m_name == m_name)
 				{
-					m_pheromoneLoveEffect.Create(base.transform.position, base.transform.rotation);
+					m_pheromoneLoveEffect.Create(transform.position, transform.rotation);
 					if (GetBaseAI() is MonsterAI monsterAI)
 					{
 						monsterAI.Alert();
@@ -954,9 +954,9 @@
 	{
 		m_lavaTimer += dt;
 		m_aboveOrInLavaTimer += dt;
-		m_lastGroundHeight = base.transform.position;
+		m_lastGroundHeight = transform.position;
 		ZoneSystem.instance.GetGroundData(ref m_lastGroundHeight, out var _, out m_lastBiome, out var _, out m_lastHeightmap);
-		if (!WorldGenerator.IsAshlands(base.transform.position.x, base.transform.position.z))
+		if (!WorldGenerator.IsAshlands(transform.position.x, transform.position.z))
 		{
 			return;
 		}
@@ -969,10 +969,10 @@
 		{
 			m_aboveOrInLavaTimer = 0f;
 		}
-		m_lavaHeightFactor = base.transform.position.y - m_lastGroundHeight.y;
+		m_lavaHeightFactor = transform.position.y - m_lastGroundHeight.y;
 		m_lavaHeightFactor = (m_lavaAirDamageHeight - m_lavaHeightFactor) / m_lavaAirDamageHeight;
 		bool flag = false;
-		if (m_lavaProximity > m_minLavaMaskThreshold && Physics.Raycast(base.transform.position + Vector3.up, Vector3.down, out var hitInfo, 50f, s_blockedRayMask) && hitInfo.collider.GetComponent<Heightmap>() == null)
+		if (m_lavaProximity > m_minLavaMaskThreshold && Physics.Raycast(transform.position + Vector3.up, Vector3.down, out var hitInfo, 50f, s_blockedRayMask) && hitInfo.collider.GetComponent<Heightmap>() == null)
 		{
 			flag = true;
 		}
@@ -1035,7 +1035,7 @@
 		}
 		if (num > 0f && m_lavaHeatParticles.Count == 0 && !IsDead())
 		{
-			GameObject[] array = m_lavaHeatEffects.Create(base.transform.position, Quaternion.identity, base.transform);
+			GameObject[] array = m_lavaHeatEffects.Create(transform.position, Quaternion.identity, transform);
 			foreach (KeyValuePair<ParticleSystem, float> lavaHeatParticle in m_lavaHeatParticles)
 			{
 				UnityEngine.Object.Destroy(lavaHeatParticle.Key.gameObject);
@@ -1152,7 +1152,7 @@
 
 	private bool IsUnderRoof()
 	{
-		return Physics.RaycastNonAlloc(base.transform.position + Vector3.up * 0.2f, Vector3.up, m_lavaRoofCheck, 20f, LayerMask.GetMask("Default", "static_solid", "piece")) > 0;
+		return Physics.RaycastNonAlloc(transform.position + Vector3.up * 0.2f, Vector3.up, m_lavaRoofCheck, 20f, LayerMask.GetMask("Default", "static_solid", "piece")) > 0;
 	}
 
 	private void UpdateAshlandsWater(float dt)
@@ -1168,7 +1168,7 @@
 			{
 				return;
 			}
-			float num = WorldGenerator.GetAshlandsOceanGradient(base.transform.position);
+			float num = WorldGenerator.GetAshlandsOceanGradient(transform.position);
 			if (!IsSwimming())
 			{
 				num *= m_heatWaterTouchMultiplier;
@@ -1188,12 +1188,12 @@
 
 	private void UpdateContinousEffects()
 	{
-		SetupContinuousEffect(base.transform, base.transform.position, m_sliding, m_slideEffects, ref m_slideEffects_instances, GetZDOID());
-		Vector3 position = base.transform.position;
+		SetupContinuousEffect(transform, transform.position, m_sliding, m_slideEffects, ref m_slideEffects_instances, GetZDOID());
+		Vector3 position = transform.position;
 		position.y = GetLiquidLevel() + 0.05f;
 		EffectList effects = ((InTar() && m_tarEffects.HasEffects()) ? m_tarEffects : m_waterEffects);
-		SetupContinuousEffect(base.transform, position, InLiquid(), effects, ref m_waterEffects_instances, GetZDOID());
-		SetupContinuousEffect(base.transform, base.transform.position, IsFlying(), m_flyingContinuousEffect, ref m_flyingEffects_instances, GetZDOID());
+		SetupContinuousEffect(transform, position, InLiquid(), effects, ref m_waterEffects_instances, GetZDOID());
+		SetupContinuousEffect(transform, transform.position, IsFlying(), m_flyingContinuousEffect, ref m_flyingEffects_instances, GetZDOID());
 	}
 
 	public static void SetupContinuousEffect(Transform transform, Vector3 point, bool enabledEffect, EffectList effects, ref GameObject[] instances, ZDOID gamepadEffectsExclusiveToPlayer = default(ZDOID))
@@ -1288,7 +1288,15 @@
 	{
 		if (!(m_lastGroundCollider == null) && !(m_lastGroundCollider.material == null) && !(m_lastGroundCollider.material.dynamicFriction > 0f) && !m_iceShoes && (s_slipperyStuffMask & m_lastGroundCollider.gameObject.layer) != 0)
 		{
-			float num = ((!m_skating) ? (isRunning ? m_slipperyControlRun : m_slipperyControl) : (isRunning ? m_skatingControlRun : m_skatingControl));
+			float num;
+			if (m_skating)
+			{
+				num = (isRunning ? m_skatingControlRun : m_skatingControl);
+			}
+			else
+			{
+				num = (isRunning ? m_slipperyControlRun : m_slipperyControl);
+			}
 			if (move.magnitude > 0.01f)
 			{
 				currentVel = currentVel * num + bodyVel * (1f - num);
@@ -1322,8 +1330,7 @@
 	private void ApplySlide(float dt, ref Vector3 currentVel, Vector3 bodyVel, bool running)
 	{
 		bool flag = CanWallRun();
-		Vector3 obj = ((m_groundTilt != GroundTiltType.None) ? m_groundTiltNormal : m_lastGroundNormal);
-		float num = Mathf.Clamp(Mathf.Acos(Mathf.Clamp01(obj.y)) * 57.29578f, 0f, 90f);
+		float num = Mathf.Clamp(Mathf.Acos(Mathf.Clamp01(((m_groundTilt != GroundTiltType.None) ? m_groundTiltNormal : m_lastGroundNormal).y)) * 57.29578f, 0f, 90f);
 		Vector3 lastGroundNormal = m_lastGroundNormal;
 		lastGroundNormal.y = 0f;
 		lastGroundNormal.Normalize();
@@ -1379,13 +1386,13 @@
 		}
 		if (InIntro())
 		{
-			m_maxAirAltitude = base.transform.position.y;
+			m_maxAirAltitude = transform.position.y;
 			m_body.linearVelocity = Vector3.zero;
 			m_body.angularVelocity = Vector3.zero;
 		}
 		if (!InLiquidSwimDepth() && !IsOnGround() && !IsAttached())
 		{
-			float y = base.transform.position.y;
+			float y = transform.position.y;
 			m_maxAirAltitude = Mathf.Max(m_maxAirAltitude, y);
 			m_fallTimer += dt;
 			if (IsPlayer() && m_fallTimer > 0.1f)
@@ -1438,7 +1445,7 @@
 		StaticPhysics component = m_lastGroundBody.GetComponent<StaticPhysics>();
 		if ((object)component != null && component.IsFalling)
 		{
-			base.transform.position = base.transform.position + m_lastGroundBody.linearVelocity * dt;
+			transform.position += m_lastGroundBody.linearVelocity * dt;
 			if (m_fallTimer > 0.1f)
 			{
 				m_zanim.SetBool(s_animatorFalling, value: false);
@@ -1471,8 +1478,8 @@
 		m_body.linearVelocity = m_currentVel;
 		m_body.useGravity = false;
 		m_lastGroundTouch = 0f;
-		m_maxAirAltitude = base.transform.position.y;
-		m_body.rotation = Quaternion.RotateTowards(base.transform.rotation, m_lookYaw, m_turnSpeed * dt);
+		m_maxAirAltitude = transform.position.y;
+		m_body.rotation = Quaternion.RotateTowards(transform.rotation, m_lookYaw, m_turnSpeed * dt);
 		m_body.angularVelocity = Vector3.zero;
 		UpdateEyeRotation();
 	}
@@ -1480,11 +1487,11 @@
 	private void UpdateSwimming(float dt)
 	{
 		bool flag = IsOnGround();
-		if (Mathf.Max(0f, m_maxAirAltitude - base.transform.position.y) > 0.5f && m_onLand != null)
-		{
-			m_onLand(new Vector3(base.transform.position.x, GetLiquidLevel(), base.transform.position.z));
-		}
-		m_maxAirAltitude = base.transform.position.y;
+		if (Mathf.Max(0f, m_maxAirAltitude - transform.position.y) > 0.5f && m_onLand != null)
+		{
+			m_onLand(new Vector3(transform.position.x, GetLiquidLevel(), transform.position.z));
+		}
+		m_maxAirAltitude = transform.position.y;
 		float speed = m_swimSpeed * GetAttackSpeedFactorMovement();
 		if (InMinorActionSlowdown())
 		{
@@ -1520,9 +1527,9 @@
 		}
 		m_body.AddForce(force, ForceMode.VelocityChange);
 		float num = GetLiquidLevel() - m_swimDepth;
-		if (base.transform.position.y < num)
-		{
-			float t = Mathf.Clamp01((num - base.transform.position.y) / 2f);
+		if (transform.position.y < num)
+		{
+			float t = Mathf.Clamp01((num - transform.position.y) / 2f);
 			float target = Mathf.Lerp(0f, 10f, t);
 			Vector3 linearVelocity = m_body.linearVelocity;
 			linearVelocity.y = Mathf.MoveTowards(linearVelocity.y, target, 50f * dt);
@@ -1530,7 +1537,7 @@
 		}
 		else
 		{
-			float t2 = Mathf.Clamp01((0f - (num - base.transform.position.y)) / 1f);
+			float t2 = Mathf.Clamp01((0f - (num - transform.position.y)) / 1f);
 			float num2 = Mathf.Lerp(0f, 10f, t2);
 			Vector3 linearVelocity2 = m_body.linearVelocity;
 			linearVelocity2.y = Mathf.MoveTowards(linearVelocity2.y, 0f - num2, 30f * dt);
@@ -1546,8 +1553,8 @@
 		m_body.angularVelocity = Vector3.zero;
 		UpdateEyeRotation();
 		m_body.useGravity = true;
-		float value = ((IsPlayer() || HaveRider()) ? Vector3.Dot(m_currentVel, base.transform.forward) : Vector3.Dot(m_body.linearVelocity, base.transform.forward));
-		float value2 = Vector3.Dot(m_currentVel, base.transform.right);
+		float value = ((IsPlayer() || HaveRider()) ? Vector3.Dot(m_currentVel, transform.forward) : Vector3.Dot(m_body.linearVelocity, transform.forward));
+		float value2 = Vector3.Dot(m_currentVel, transform.right);
 		m_currentTurnVel = Mathf.SmoothDamp(m_currentTurnVel, target2, ref m_currentTurnVelChange, 0.5f, 99f);
 		m_zanim.SetFloat(s_forwardSpeed, value);
 		m_zanim.SetFloat(s_sidewaySpeed, value2);
@@ -1567,7 +1574,7 @@
 		float num = (m_run ? m_flyFastSpeed : m_flySlowSpeed) * GetAttackSpeedFactorMovement();
 		Vector3 b = (CanMove() ? (m_moveDir * num) : Vector3.zero);
 		m_currentVel = Vector3.Lerp(m_currentVel, b, m_acceleration);
-		m_maxAirAltitude = base.transform.position.y;
+		m_maxAirAltitude = transform.position.y;
 		ApplyRootMotion(ref m_currentVel);
 		AddPushbackForce(ref m_currentVel);
 		Vector3 force = m_currentVel - m_body.linearVelocity;
@@ -1586,9 +1593,9 @@
 		m_body.angularVelocity = Vector3.zero;
 		UpdateEyeRotation();
 		m_body.useGravity = false;
-		float num2 = Vector3.Dot(m_currentVel, base.transform.forward);
-		float value = Vector3.Dot(m_currentVel, base.transform.right);
-		float num3 = Vector3.Dot(m_body.linearVelocity, base.transform.forward);
+		float num2 = Vector3.Dot(m_currentVel, transform.forward);
+		float value = Vector3.Dot(m_currentVel, transform.right);
+		float num3 = Vector3.Dot(m_body.linearVelocity, transform.forward);
 		m_currentTurnVel = Mathf.SmoothDamp(m_currentTurnVel, target, ref m_currentTurnVelChange, 0.5f, 99f);
 		m_zanim.SetFloat(s_forwardSpeed, IsPlayer() ? num2 : num3);
 		m_zanim.SetFloat(s_sidewaySpeed, value);
@@ -1605,11 +1612,11 @@
 		bool flag = IsCrouching();
 		m_running = CheckRun(vector, dt);
 		m_slipping = m_lastGroundCollider != null && m_lastGroundCollider.material != null && m_lastGroundCollider.material.dynamicFriction <= 0f && (s_slipperyStuffMask & m_lastGroundCollider.gameObject.layer) != 0;
-		Vector3 vector2 = (base.transform.position - m_lastPos) / dt;
+		Vector3 vector2 = (transform.position - m_lastPos) / dt;
 		float magnitude = vector2.magnitude;
 		vector2.y = 0f;
 		vector2 = vector2.normalized * magnitude;
-		Vector3 vector3 = base.transform.position - m_lazyPos;
+		Vector3 vector3 = transform.position - m_lazyPos;
 		vector3.y = 0f;
 		float num = Vector3.Dot(vector, vector3.normalized);
 		if (m_slipping && !m_iceShoes && vector == Vector3.zero && vector2.magnitude > (m_skating ? m_skatingMinSpeed : m_slippingMinSpeed))
@@ -1670,7 +1677,7 @@
 				m_slipperySpeed *= (m_skating ? m_skatingBreaking : m_slipperyBreaking);
 				speed = m_slipperySpeed;
 				Quaternion to = Quaternion.LookRotation(vector3);
-				m_body.rotation = Quaternion.RotateTowards(base.transform.rotation, to, m_skating ? m_skatingTurnDir : m_slipperyTurnDir);
+				m_body.rotation = Quaternion.RotateTowards(transform.rotation, to, m_skating ? m_skatingTurnDir : m_slipperyTurnDir);
 			}
 		}
 		else if (!IsOnGround())
@@ -1694,21 +1701,21 @@
 		{
 			if (m_deepSnowSlowMax != 0f && m_lastHeightmap != null)
 			{
-				float num7 = m_lastHeightmap.GetCultivationMask(base.transform.position) * m_deepSnowSlowMaxHeight;
+				float num7 = m_lastHeightmap.GetCultivationMask(transform.position) * m_deepSnowSlowMaxHeight;
 				if (num7 > m_deepSnowSlowStartHeight)
 				{
-					if ((bool)m_deepSnowWalkObj && Vector3.Distance(m_lastDeepSnowWalkPos, base.transform.position) > m_deepSnowWalkObjDist)
+					if ((bool)m_deepSnowWalkObj && Vector3.Distance(m_lastDeepSnowWalkPos, transform.position) > m_deepSnowWalkObjDist)
 					{
 						if (IsOnHeightmap())
 						{
-							UnityEngine.Object.Instantiate(m_deepSnowWalkObj, base.transform.position, base.transform.rotation);
+							UnityEngine.Object.Instantiate(m_deepSnowWalkObj, transform.position, transform.rotation);
 						}
-						m_lastDeepSnowWalkPos = base.transform.position;
+						m_lastDeepSnowWalkPos = transform.position;
 					}
 					float num8 = m_lastGroundHeight.y + num7;
-					if (base.transform.position.y < num8)
+					if (transform.position.y < num8)
 					{
-						float num9 = (num8 - base.transform.position.y - m_deepSnowSlowStartHeight) / (m_deepSnowSlowMaxHeight - m_deepSnowSlowStartHeight) * m_deepSnowSlowMax;
+						float num9 = (num8 - transform.position.y - m_deepSnowSlowStartHeight) / (m_deepSnowSlowMaxHeight - m_deepSnowSlowStartHeight) * m_deepSnowSlowMax;
 						speed *= 1f - num9;
 						if (Terminal.m_showTests && IsPlayer())
 						{
@@ -1717,10 +1724,10 @@
 					}
 				}
 			}
-			if (IsPlayer() && Vector3.Distance(m_lastSnowPieceRemove, base.transform.position) > m_snowWalkPieceDist)
-			{
-				m_lastSnowPieceRemove = base.transform.position;
-				int num10 = Physics.OverlapSphereNonAlloc(base.transform.position, m_snowWalkPieceRadius, s_pieceColliders, m_snowPieceRayMask);
+			if (IsPlayer() && Vector3.Distance(m_lastSnowPieceRemove, transform.position) > m_snowWalkPieceDist)
+			{
+				m_lastSnowPieceRemove = transform.position;
+				int num10 = Physics.OverlapSphereNonAlloc(transform.position, m_snowWalkPieceRadius, s_pieceColliders, m_snowPieceRayMask);
 				for (int i = 0; i < num10; i++)
 				{
 					Collider collider = s_pieceColliders[i];
@@ -1806,10 +1813,10 @@
 		Vector3 vel = m_body.linearVelocity;
 		m_seman.ModifyWalkVelocity(ref vel);
 		m_body.linearVelocity = vel;
-		if ((bool)m_lastGroundBody && m_lastGroundBody.gameObject.layer != base.gameObject.layer && m_lastGroundBody.mass > m_body.mass)
+		if ((bool)m_lastGroundBody && m_lastGroundBody.gameObject.layer != gameObject.layer && m_lastGroundBody.mass > m_body.mass)
 		{
 			float num12 = m_body.mass / m_lastGroundBody.mass;
-			m_lastGroundBody.AddForceAtPosition(-vector5 * num12 * m_lastGroundBody.mass, base.transform.position, ForceMode.Impulse);
+			m_lastGroundBody.AddForceAtPosition(-vector5 * num12 * m_lastGroundBody.mass, transform.position, ForceMode.Impulse);
 		}
 		float target = 0f;
 		if (((m_moveDir.magnitude > 0.1f || AlwaysRotateCamera() || m_standUp > 0f) && !InDodge() && CanMove()) || m_groundContact)
@@ -1824,7 +1831,7 @@
 		}
 		UpdateEyeRotation();
 		m_body.useGravity = true;
-		float num13 = Vector3.Dot(m_currentVel, Vector3.ProjectOnPlane(base.transform.forward, m_lastGroundNormal).normalized);
+		float num13 = Vector3.Dot(m_currentVel, Vector3.ProjectOnPlane(transform.forward, m_lastGroundNormal).normalized);
 		float num14 = Vector3.Dot(m_body.linearVelocity, m_visual.transform.forward);
 		if (IsRiding())
 		{
@@ -1834,7 +1841,7 @@
 		{
 			num13 = Mathf.Min(num13, num14);
 		}
-		float value = Vector3.Dot(m_currentVel, Vector3.ProjectOnPlane(base.transform.right, m_lastGroundNormal).normalized);
+		float value = Vector3.Dot(m_currentVel, Vector3.ProjectOnPlane(transform.right, m_lastGroundNormal).normalized);
 		m_currentTurnVel = Mathf.SmoothDamp(m_currentTurnVel, target, ref m_currentTurnVelChange, 0.5f, 99f);
 		m_zanim.SetFloat(s_forwardSpeed, num13);
 		m_zanim.SetFloat(s_sidewaySpeed, value);
@@ -1857,11 +1864,11 @@
 				AddNoise(15f);
 			}
 		}
-		m_lastPos = base.transform.position;
+		m_lastPos = transform.position;
 		float num15 = Mathf.Clamp(m_body.linearVelocity.magnitude, m_skating ? m_skatingMomentumDistanceMin : m_slippingMomentumDistanceMin, m_skating ? m_skatingMomentumDistance : m_slippingMomentumDistance);
-		if (Vector3.Distance(base.transform.position, m_lazyPos) > num15)
-		{
-			m_lazyPos = base.transform.position - (base.transform.position - m_lazyPos).normalized * num15;
+		if (Vector3.Distance(transform.position, m_lazyPos) > num15)
+		{
+			m_lazyPos = transform.position - (transform.position - m_lazyPos).normalized * num15;
 		}
 	}
 
@@ -1880,7 +1887,7 @@
 		{
 			return 0f;
 		}
-		float num = Vector3.SignedAngle(base.transform.forward, m_lastGroundNormal, base.transform.right);
+		float num = Vector3.SignedAngle(transform.forward, m_lastGroundNormal, transform.right);
 		return 0f - (90f - (0f - num));
 	}
 
@@ -1936,7 +1943,7 @@
 		Vector3 vector = Vector3.zero;
 		if (IsOnGround() && (bool)m_lastGroundBody && m_groundForceTimer <= 0f)
 		{
-			vector = m_lastGroundBody.GetPointVelocity(base.transform.position);
+			vector = m_lastGroundBody.GetPointVelocity(transform.position);
 			vector.y = 0f;
 		}
 		Ship standingOnShip = GetStandingOnShip();
@@ -1985,7 +1992,7 @@
 	private float UpdateRotation(float turnSpeed, float dt, bool smooth)
 	{
 		Quaternion quaternion = ((AlwaysRotateCamera() || m_moveDir == Vector3.zero) ? m_lookYaw : Quaternion.LookRotation(m_moveDir));
-		float yawDeltaAngle = Utils.GetYawDeltaAngle(base.transform.rotation, quaternion);
+		float yawDeltaAngle = Utils.GetYawDeltaAngle(transform.rotation, quaternion);
 		float num = 1f;
 		if (!IsPlayer())
 		{
@@ -2004,10 +2011,10 @@
 			}
 		}
 		float num2 = turnSpeed * GetAttackSpeedFactorRotation() * num;
-		Quaternion rotation = Quaternion.RotateTowards(base.transform.rotation, quaternion, num2 * dt);
+		Quaternion rotation = Quaternion.RotateTowards(transform.rotation, quaternion, num2 * dt);
 		if (Mathf.Abs(yawDeltaAngle) > 0.001f)
 		{
-			base.transform.rotation = rotation;
+			transform.rotation = rotation;
 		}
 		return num2 * Mathf.Sign(yawDeltaAngle) * (MathF.PI / 180f);
 	}
@@ -2027,13 +2034,13 @@
 					Vector3 vector = m_lastGroundNormal;
 					if (m_groundTilt == GroundTiltType.PitchRaycast || m_groundTilt == GroundTiltType.FullRaycast)
 					{
-						Vector3 p = base.transform.position + base.transform.forward * m_collider.radius;
-						Vector3 p2 = base.transform.position - base.transform.forward * m_collider.radius;
+						Vector3 p = transform.position + transform.forward * m_collider.radius;
+						Vector3 p2 = transform.position - transform.forward * m_collider.radius;
 						GetGroundHeight(p, out var _, out var normal);
 						GetGroundHeight(p2, out var _, out var normal2);
 						vector = (vector + normal + normal2).normalized;
 					}
-					Vector3 target = base.transform.InverseTransformVector(vector);
+					Vector3 target = transform.InverseTransformVector(vector);
 					target = Vector3.RotateTowards(Vector3.up, target, 0.87266463f, 1f);
 					m_groundTiltNormal = Vector3.Lerp(m_groundTiltNormal, target, 0.05f);
 					Vector3 vector3;
@@ -2051,7 +2058,7 @@
 				}
 				else if (IsFlying() && !IsOnGround() && m_groundTilt == GroundTiltType.Flying && m_currentVel.sqrMagnitude > 0f)
 				{
-					m_groundTiltNormal = Vector3.Cross(base.transform.InverseTransformVector(m_currentVel.normalized), Vector3.right);
+					m_groundTiltNormal = Vector3.Cross(transform.InverseTransformVector(m_currentVel.normalized), Vector3.right);
 					Quaternion b = Quaternion.LookRotation(Vector3.Cross(m_groundTiltNormal, Vector3.left), m_groundTiltNormal);
 					b = Quaternion.Lerp(Quaternion.identity, b, m_currentVel.magnitude * 0.33f);
 					m_visual.transform.localRotation = Quaternion.RotateTowards(m_visual.transform.localRotation, b, dt * m_groundTiltSpeed);
@@ -2080,7 +2087,7 @@
 				if (m_wallRunning)
 				{
 					Vector3 vector4 = Vector3.Lerp(Vector3.up, m_lastGroundNormal, 0.65f);
-					Vector3 forward = Vector3.ProjectOnPlane(base.transform.forward, vector4);
+					Vector3 forward = Vector3.ProjectOnPlane(transform.forward, vector4);
 					forward.Normalize();
 					Quaternion to2 = Quaternion.LookRotation(forward, vector4);
 					m_visual.transform.rotation = Quaternion.RotateTowards(m_visual.transform.rotation, to2, 30f * dt);
@@ -2167,7 +2174,7 @@
 
 	public Vector3 GetTopPoint()
 	{
-		return base.transform.TransformPoint(m_collider.center) + m_visual.transform.up * (m_collider.height * 0.5f);
+		return transform.TransformPoint(m_collider.center) + m_visual.transform.up * (m_collider.height * 0.5f);
 	}
 
 	public float GetRadius()
@@ -2176,7 +2183,7 @@
 		{
 			return m_collider.radius;
 		}
-		return m_collider.radius * base.transform.localScale.magnitude;
+		return m_collider.radius * transform.localScale.magnitude;
 	}
 
 	public float GetHeight()
@@ -2276,7 +2283,7 @@
 		}
 		if (attacker != null && !attacker.IsPlayer())
 		{
-			float difficultyDamageScalePlayer = Game.instance.GetDifficultyDamageScalePlayer(base.transform.position);
+			float difficultyDamageScalePlayer = Game.instance.GetDifficultyDamageScalePlayer(transform.position);
 			hit.ApplyModifier(difficultyDamageScalePlayer);
 			hit.ApplyModifier(Game.m_enemyDamageRate);
 		}
@@ -2331,18 +2338,18 @@
 		m_seman.OnDamaged(hit, attacker);
 		if (m_baseAI != null && m_baseAI.IsAggravatable() && !m_baseAI.IsAggravated() && (bool)attacker && attacker.IsPlayer() && hit.GetTotalDamage() > 0f)
 		{
-			BaseAI.AggravateAllInArea(base.transform.position, 20f, BaseAI.AggravatedReason.Damage);
+			BaseAI.AggravateAllInArea(transform.position, 20f, BaseAI.AggravatedReason.Damage);
 		}
 		if (m_baseAI != null && !m_baseAI.IsAlerted() && hit.m_backstabBonus > 1f && Time.time - m_backstabTime > 300f && (!ZoneSystem.instance.GetGlobalKey(GlobalKeys.PassiveMobs) || !m_baseAI.CanSeeTarget(attacker)))
 		{
 			m_backstabTime = Time.time;
 			hit.ApplyModifier(hit.m_backstabBonus);
-			m_backstabHitEffects.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, attacker?.GetZDOID() ?? ZDOID.None);
+			m_backstabHitEffects.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, attacker?.GetZDOID() ?? ZDOID.None);
 		}
 		if (IsStaggering() && !IsPlayer())
 		{
 			hit.ApplyModifier(2f);
-			m_critHitEffects.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, attacker?.GetZDOID() ?? ZDOID.None);
+			m_critHitEffects.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, attacker?.GetZDOID() ?? ZDOID.None);
 		}
 		if (hit.m_blockable && IsBlocking())
 		{
@@ -2423,7 +2430,7 @@
 		float totalDamage = hit.GetTotalDamage();
 		if (!IsPlayer())
 		{
-			float difficultyDamageScaleEnemy = Game.instance.GetDifficultyDamageScaleEnemy(base.transform.position);
+			float difficultyDamageScaleEnemy = Game.instance.GetDifficultyDamageScaleEnemy(transform.position);
 			hit.ApplyModifier(difficultyDamageScaleEnemy);
 			hit.ApplyModifier(Game.m_playerDamageRate);
 		}
@@ -2472,7 +2479,7 @@
 			DoDamageCameraShake(hit);
 			if (hit.m_damage.GetTotalPhysicalDamage() > 0f)
 			{
-				m_hitEffects.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, GetZDOID());
+				m_hitEffects.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, GetZDOID());
 			}
 		}
 		OnDamaged(hit);
@@ -2677,7 +2684,7 @@
 			if (forceDirection.magnitude > 0.01f)
 			{
 				forceDirection.y = 0f;
-				base.transform.rotation = Quaternion.LookRotation(-forceDirection);
+				transform.rotation = Quaternion.LookRotation(-forceDirection);
 			}
 			m_zanim.SetSpeed(1f);
 			m_zanim.SetTrigger("stagger");
@@ -2724,7 +2731,7 @@
 		for (int i = 0; i < contacts.Length; i++)
 		{
 			ContactPoint contactPoint = contacts[i];
-			float num = contactPoint.point.y - base.transform.position.y;
+			float num = contactPoint.point.y - transform.position.y;
 			Vector3 normal = contactPoint.normal;
 			if (normal.y < 0f)
 			{
@@ -2773,12 +2780,12 @@
 		m_lastGroundNormal = m_groundContactNormal;
 		m_lastGroundPoint = m_groundContactPoint;
 		m_lastGroundBody = (m_lastGroundCollider ? m_lastGroundCollider.attachedRigidbody : null);
-		if (!IsPlayer() && m_lastGroundBody != null && m_lastGroundBody.gameObject.layer == base.gameObject.layer)
+		if (!IsPlayer() && m_lastGroundBody != null && m_lastGroundBody.gameObject.layer == gameObject.layer)
 		{
 			m_lastGroundCollider = null;
 			m_lastGroundBody = null;
 		}
-		float num = Mathf.Max(0f, m_maxAirAltitude - base.transform.position.y);
+		float num = Mathf.Max(0f, m_maxAirAltitude - transform.position.y);
 		if (num > 0.8f)
 		{
 			if (m_onLand != null)
@@ -2790,9 +2797,9 @@
 				}
 				m_onLand(m_lastGroundPoint);
 			}
-			if (m_lastBiome == Heightmap.Biome.DeepNorth && m_deepSnowSlowMax != 0f && m_lastHeightmap != null && (bool)m_deepSnowWalkObj && m_lastHeightmap.GetCultivationMask(base.transform.position) * m_deepSnowSlowMaxHeight > m_deepSnowSlowStartHeight)
-			{
-				UnityEngine.Object.Instantiate(m_deepSnowWalkObj, base.transform.position, base.transform.rotation);
+			if (m_lastBiome == Heightmap.Biome.DeepNorth && m_deepSnowSlowMax != 0f && m_lastHeightmap != null && (bool)m_deepSnowWalkObj && m_lastHeightmap.GetCultivationMask(transform.position) * m_deepSnowSlowMaxHeight > m_deepSnowSlowStartHeight)
+			{
+				UnityEngine.Object.Instantiate(m_deepSnowWalkObj, transform.position, transform.rotation);
 			}
 		}
 		if (IsPlayer() && num > 4f)
@@ -2811,7 +2818,7 @@
 		}
 		ResetGroundContact();
 		m_lastGroundTouch = 0f;
-		m_maxAirAltitude = base.transform.position.y;
+		m_maxAirAltitude = transform.position.y;
 		if (IsPlayer() && Terminal.m_showTests)
 		{
 			Dictionary<string, string> testList = Terminal.m_testList;
@@ -2907,9 +2914,9 @@
 	public virtual void OnDeath()
 	{
 		PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
-		Character obj = m_lastHit?.GetAttacker();
+		Character character = m_lastHit?.GetAttacker();
 		bool flag = m_nview.GetZDO().GetBool(ZDOVars.s_cheated);
-		bool flag2 = obj == Player.m_localPlayer;
+		bool flag2 = character == Player.m_localPlayer;
 		if (flag2 && IsPlayer() && this is Player player)
 		{
 			flag &= !PlayerProfile.s_bypassCheatChecks;
@@ -2950,13 +2957,13 @@
 				instance.RegisterKill(characterID.UserID, m_name, BossOrder(), modifiers, attackers, flag);
 			}
 		}
-		SetupContinuousEffect(base.transform, base.transform.position, enabledEffect: false, m_flyingContinuousEffect, ref m_flyingEffects_instances);
+		SetupContinuousEffect(transform, transform.position, enabledEffect: false, m_flyingContinuousEffect, ref m_flyingEffects_instances);
 		CharacterDrop component = GetComponent<CharacterDrop>();
 		if ((bool)component)
 		{
 			component.m_cheated = flag;
 		}
-		GameObject[] array = m_deathEffects.Create(base.transform.position, base.transform.rotation, base.transform);
+		GameObject[] array = m_deathEffects.Create(transform.position, transform.rotation, transform);
 		for (int s_attackers = 0; s_attackers < array.Length; s_attackers++)
 		{
 			Ragdoll component2 = array[s_attackers].GetComponent<Ragdoll>();
@@ -2996,7 +3003,7 @@
 			ZoneSystem.instance.GetGlobalKey(GlobalKeys.activeBosses, out float value2);
 			ZoneSystem.instance.SetGlobalKey(GlobalKeys.activeBosses, Mathf.Max(0f, value2 - 1f));
 		}
-		ZNetScene.instance.Destroy(base.gameObject);
+		ZNetScene.instance.Destroy(gameObject);
 		Gogan.LogEvent("Game", "Killed", m_name, 0L);
 	}
 
@@ -3154,7 +3161,7 @@
 		}
 		if (dir.magnitude <= Mathf.Epsilon)
 		{
-			dir = base.transform.forward;
+			dir = transform.forward;
 		}
 		else
 		{
@@ -3229,7 +3236,7 @@
 				m_body.linearVelocity = zero;
 				m_lastGroundTouch = 1f;
 				m_jumpTimer = 0f;
-				m_jumpEffects.Create(base.transform.position, base.transform.rotation, base.transform, 1f, -1, GetZDOID());
+				m_jumpEffects.Create(transform.position, transform.rotation, transform, 1f, -1, GetZDOID());
 				SetCrouch(crouch: false);
 				UpdateBodyFriction();
 			}
@@ -3279,7 +3286,15 @@
 			{
 				jump += normalized * (num3 - num4);
 			}
-			Vector3 vector = ((!IsPlayer()) ? base.transform.forward : (m_slipping ? m_currentVel.normalized : m_moveDir));
+			Vector3 vector;
+			if (IsPlayer())
+			{
+				vector = (m_slipping ? m_currentVel.normalized : m_moveDir);
+			}
+			else
+			{
+				vector = transform.forward;
+			}
 			jump += vector * m_jumpForceForward * num2;
 			if (flag)
 			{
@@ -3291,7 +3306,7 @@
 				ForceJump(jump);
 			}
 		}
-		else if ((bool)GrapplingPoint.m_localGrappler && Vector3.Distance(GrapplingPoint.m_localGrappler.transform.position, base.transform.position) > GrapplingPoint.m_localGrappler.m_jumpPullMaxDist)
+		else if ((bool)GrapplingPoint.m_localGrappler && Vector3.Distance(GrapplingPoint.m_localGrappler.transform.position, transform.position) > GrapplingPoint.m_localGrappler.m_jumpPullMaxDist)
 		{
 			if (!HaveStamina(m_jumpStaminaUsage) && IsPlayer())
 			{
@@ -3314,7 +3329,7 @@
 		if (effects)
 		{
 			m_zanim.SetTrigger("jump");
-			m_jumpEffects.Create(base.transform.position, base.transform.rotation, base.transform, 1f, -1, GetZDOID());
+			m_jumpEffects.Create(transform.position, transform.rotation, transform, 1f, -1, GetZDOID());
 			ResetCloth();
 			OnJump();
 			SetCrouch(crouch: false);
@@ -3324,13 +3339,13 @@
 
 	public void SetTempParent(Transform t)
 	{
-		oldParent = base.transform.parent;
-		base.transform.parent = t;
+		oldParent = transform.parent;
+		transform.parent = t;
 	}
 
 	public void ReleaseTempParent()
 	{
-		base.transform.parent = oldParent;
+		transform.parent = oldParent;
 	}
 
 	private void UpdateBodyFriction()
@@ -3581,7 +3596,7 @@
 		}
 		else
 		{
-			m_cashedInLiquidDepth = Mathf.Max(0f, GetLiquidLevel() - base.transform.position.y);
+			m_cashedInLiquidDepth = Mathf.Max(0f, GetLiquidLevel() - transform.position.y);
 		}
 	}
 
@@ -3939,16 +3954,16 @@
 		if (m_nview != null && m_nview.GetZDO() != null)
 		{
 			float radius = m_nview.GetZDO().GetFloat(ZDOVars.s_noise);
-			Gizmos.DrawWireSphere(base.transform.position, radius);
+			Gizmos.DrawWireSphere(transform.position, radius);
 		}
 		Gizmos.color = Color.blue;
-		Gizmos.DrawWireCube(base.transform.position + Vector3.up * m_swimDepth, new Vector3(1f, 0.05f, 1f));
+		Gizmos.DrawWireCube(transform.position + Vector3.up * m_swimDepth, new Vector3(1f, 0.05f, 1f));
 		if (IsOnGround())
 		{
 			Gizmos.color = Color.green;
 			Gizmos.DrawLine(m_lastGroundPoint, m_lastGroundPoint + m_lastGroundNormal);
 		}
-		Gizmos.DrawLine(base.transform.position, m_lazyPos);
+		Gizmos.DrawLine(transform.position, m_lazyPos);
 	}
 
 	public virtual bool TeleportTo(Vector3 pos, Quaternion rot, bool distantTeleport)
@@ -4177,7 +4192,7 @@
 				if ((object)skills != null)
 				{
 					skills.RaiseSkill(m_tameable.m_levelUpOwnerSkill, value * m_tameable.m_levelUpFactor);
-					Terminal.Log($"{base.name} leveling up from '{skill}' to master {component.name} skill '{m_tameable.m_levelUpOwnerSkill}' at factor {value * m_tameable.m_levelUpFactor}");
+					Terminal.Log($"{name} leveling up from '{skill}' to master {component.name} skill '{m_tameable.m_levelUpOwnerSkill}' at factor {value * m_tameable.m_levelUpFactor}");
 				}
 			}
 		}
@@ -4222,7 +4237,7 @@
 		{
 			return null;
 		}
-		return base.transform;
+		return transform;
 	}
 
 	public Collider GetLastGroundCollider()
@@ -4263,8 +4278,8 @@
 			{
 				parent = component.GetZDO().m_uid;
 				attachJoint = "";
-				relativePos = component.transform.InverseTransformPoint(base.transform.position);
-				relativeRot = Quaternion.Inverse(component.transform.rotation) * base.transform.rotation;
+				relativePos = component.transform.InverseTransformPoint(transform.position);
+				relativeRot = Quaternion.Inverse(component.transform.rotation) * transform.rotation;
 				relativeVel = component.transform.InverseTransformVector(m_body.linearVelocity - m_lastGroundBody.linearVelocity);
 				return true;
 			}
@@ -4360,7 +4375,7 @@
 
 	public bool InInterior()
 	{
-		return InInterior(base.transform);
+		return InInterior(transform);
 	}
 
 	public static bool InInterior(Transform me)
@@ -4386,7 +4401,7 @@
 	public void TakeOff()
 	{
 		m_flying = true;
-		m_jumpEffects.Create(base.transform.position, Quaternion.identity);
+		m_jumpEffects.Create(transform.position, Quaternion.identity);
 		m_animator.SetTrigger("fly_takeoff");
 	}
 
```
