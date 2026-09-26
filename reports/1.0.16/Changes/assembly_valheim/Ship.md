# `Ship.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+36/-36` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Ship.cs
+++ b/Ship.cs
@@ -166,7 +166,7 @@
 		}
 		if (m_nview.GetZDO() == null)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 		m_body.maxDepenetrationVelocity = 2f;
 		Heightmap.ForceGenerateAll();
@@ -329,18 +329,18 @@
 			m_speed = Speed.Stop;
 		}
 		Vector3 worldCenterOfMass = m_body.worldCenterOfMass;
-		Transform obj = m_floatCollider.transform;
+		Transform transform = m_floatCollider.transform;
 		Vector3 size = m_floatCollider.size;
-		Vector3 position = obj.position;
-		Vector3 forward = obj.forward;
-		Vector3 right = obj.right;
+		Vector3 position = transform.position;
+		Vector3 forward = transform.forward;
+		Vector3 right = transform.right;
 		Vector3 vector = position + forward * size.z / 2f;
 		Vector3 vector2 = position - forward * size.z / 2f;
 		Vector3 vector3 = position - right * size.x / 2f;
 		Vector3 vector4 = position + right * size.x / 2f;
-		Transform obj2 = base.transform;
-		Vector3 forward2 = obj2.forward;
-		Vector3 right2 = obj2.right;
+		Transform transform2 = base.transform;
+		Vector3 forward2 = transform2.forward;
+		Vector3 right2 = transform2.right;
 		float waterLevel = Floating.GetWaterLevel(worldCenterOfMass, ref m_previousCenter);
 		float waterLevel2 = Floating.GetWaterLevel(vector3, ref m_previousLeft);
 		float waterLevel3 = Floating.GetWaterLevel(vector4, ref m_previousRight);
@@ -432,7 +432,7 @@
 
 	private void UpdateUpsideDmg(float dt)
 	{
-		if (!(base.transform.up.y >= 0f))
+		if (!(transform.up.y >= 0f))
 		{
 			m_upsideDownDmgTimer += dt;
 			if (!(m_upsideDownDmgTimer <= m_upsideDownDmgInterval))
@@ -440,7 +440,7 @@
 				m_upsideDownDmgTimer = 0f;
 				HitData hitData = new HitData();
 				hitData.m_damage.m_blunt = m_upsideDownDmg;
-				hitData.m_point = base.transform.position;
+				hitData.m_point = transform.position;
 				hitData.m_dir = Vector3.up;
 				m_destructible.Damage(hitData);
 			}
@@ -453,7 +453,7 @@
 		{
 			return;
 		}
-		float ashlandsOceanGradient = WorldGenerator.GetAshlandsOceanGradient(base.transform.position);
+		float ashlandsOceanGradient = WorldGenerator.GetAshlandsOceanGradient(transform.position);
 		if ((bool)m_ashdamageEffects)
 		{
 			if (ashlandsOceanGradient < 0f)
@@ -486,7 +486,7 @@
 			HitData hitData = new HitData();
 			hitData.m_damage.m_blunt = Mathf.Floor(Mathf.Lerp(1f, 30f, ashlandsOceanGradient));
 			hitData.m_hitType = HitData.HitType.AshlandsOcean;
-			hitData.m_point = base.transform.position;
+			hitData.m_point = transform.position;
 			hitData.m_dir = Vector3.up;
 			m_destructible.Damage(hitData);
 		}
@@ -499,14 +499,14 @@
 		float num = Mathf.Lerp(0.25f, 1f, windIntensity);
 		float windAngleFactor = GetWindAngleFactor();
 		windAngleFactor *= num;
-		Vector3 target = Vector3.Normalize(windDir + base.transform.forward) * (windAngleFactor * m_sailForceFactor * sailSize);
+		Vector3 target = Vector3.Normalize(windDir + transform.forward) * (windAngleFactor * m_sailForceFactor * sailSize);
 		m_sailForce = Vector3.SmoothDamp(m_sailForce, target, ref m_windChangeVelocity, 1f, 99f);
 		return m_sailForce;
 	}
 
 	public float GetWindAngleFactor()
 	{
-		float num = Vector3.Dot(EnvMan.instance.GetWindDir(), -base.transform.forward);
+		float num = Vector3.Dot(EnvMan.instance.GetWindDir(), -transform.forward);
 		float num2 = Mathf.Lerp(0.7f, 1f, 1f - Utils.Abs(num));
 		float num3 = 1f - Utils.LerpStep(0.75f, 0.8f, num);
 		return num2 * num3;
@@ -522,12 +522,12 @@
 		if (!(num3 > 0f) && Utils.Abs(num3) > m_minWaterImpactForce && time - m_lastWaterImpactTime > m_minWaterImpactInterval)
 		{
 			m_lastWaterImpactTime = time;
-			m_waterImpactEffect.Create(base.transform.position, base.transform.rotation);
+			m_waterImpactEffect.Create(transform.position, transform.rotation);
 			if (m_players.Count > 0)
 			{
 				HitData hitData = new HitData();
 				hitData.m_damage.m_blunt = m_waterImpactDamage;
-				hitData.m_point = base.transform.position;
+				hitData.m_point = transform.position;
 				hitData.m_dir = Vector3.up;
 				m_destructible.Damage(hitData);
 			}
@@ -536,11 +536,11 @@
 
 	private void ApplyEdgeForce(float dt)
 	{
-		float magnitude = base.transform.position.magnitude;
+		float magnitude = transform.position.magnitude;
 		float num = 10420f;
 		if (magnitude > num)
 		{
-			Vector3 vector = Vector3.Normalize(base.transform.position);
+			Vector3 vector = Vector3.Normalize(transform.position);
 			float num2 = Utils.LerpStep(num, 10500f, magnitude) * 8f;
 			Vector3 vector2 = vector * num2;
 			m_body.AddForce(vector2 * dt, ForceMode.VelocityChange);
@@ -549,28 +549,28 @@
 
 	private void FixTilt()
 	{
-		float num = Mathf.Asin(base.transform.right.y);
-		float num2 = Mathf.Asin(base.transform.forward.y);
+		float num = Mathf.Asin(transform.right.y);
+		float num2 = Mathf.Asin(transform.forward.y);
 		if (Utils.Abs(num) > MathF.PI / 6f)
 		{
 			if (num > 0f)
 			{
-				base.transform.RotateAround(base.transform.position, base.transform.forward, (0f - Time.fixedDeltaTime) * 20f);
+				transform.RotateAround(transform.position, transform.forward, (0f - Time.fixedDeltaTime) * 20f);
 			}
 			else
 			{
-				base.transform.RotateAround(base.transform.position, base.transform.forward, Time.fixedDeltaTime * 20f);
+				transform.RotateAround(transform.position, transform.forward, Time.fixedDeltaTime * 20f);
 			}
 		}
 		if (Utils.Abs(num2) > MathF.PI / 6f)
 		{
 			if (num2 > 0f)
 			{
-				base.transform.RotateAround(base.transform.position, base.transform.right, (0f - Time.fixedDeltaTime) * 20f);
+				transform.RotateAround(transform.position, transform.right, (0f - Time.fixedDeltaTime) * 20f);
 			}
 			else
 			{
-				base.transform.RotateAround(base.transform.position, base.transform.right, Time.fixedDeltaTime * 20f);
+				transform.RotateAround(transform.position, transform.right, Time.fixedDeltaTime * 20f);
 			}
 		}
 	}
@@ -603,17 +603,17 @@
 	{
 		UpdateSailSize(dt);
 		Vector3 windDir = EnvMan.instance.GetWindDir();
-		windDir = Vector3.Cross(Vector3.Cross(windDir, base.transform.up), base.transform.up);
+		windDir = Vector3.Cross(Vector3.Cross(windDir, transform.up), transform.up);
 		if (m_speed == Speed.Full || m_speed == Speed.Half)
 		{
-			float t = 0.5f + Vector3.Dot(base.transform.forward, windDir) * 0.5f;
-			Quaternion to = Quaternion.LookRotation(-Vector3.Lerp(windDir, Vector3.Normalize(windDir - base.transform.forward), t), base.transform.up);
+			float t = 0.5f + Vector3.Dot(transform.forward, windDir) * 0.5f;
+			Quaternion to = Quaternion.LookRotation(-Vector3.Lerp(windDir, Vector3.Normalize(windDir - transform.forward), t), transform.up);
 			m_mastObject.transform.rotation = Quaternion.RotateTowards(m_mastObject.transform.rotation, to, 30f * dt);
 		}
 		else if (m_speed == Speed.Back)
 		{
-			Quaternion quaternion = Quaternion.LookRotation(-base.transform.forward, base.transform.up);
-			Quaternion to2 = Quaternion.LookRotation(-windDir, base.transform.up);
+			Quaternion quaternion = Quaternion.LookRotation(-transform.forward, transform.up);
+			Quaternion to2 = Quaternion.LookRotation(-windDir, transform.up);
 			to2 = Quaternion.RotateTowards(quaternion, to2, 80f);
 			m_mastObject.transform.rotation = Quaternion.RotateTowards(m_mastObject.transform.rotation, to2, 30f * dt);
 		}
@@ -669,7 +669,7 @@
 			{
 				ZDOID zDOID = ((Player.m_localPlayer.GetPlayerID() == m_shipControlls.GetUser()) ? Player.m_localPlayer.GetZDOID() : ZDOID.None);
 				Debug.Log($"now swapping sailpos, using {m_changeSailPosEffect.m_effectPrefabs[0].m_prefab.name}, for this local player: {zDOID}");
-				m_changeSailPosEffect.Create(base.transform.position, Quaternion.identity, null, 1f, -1, zDOID);
+				m_changeSailPosEffect.Create(transform.position, Quaternion.identity, null, 1f, -1, zDOID);
 			}
 			float t = Utils.Frac(Mathf.Clamp(m_sailPosition, 0f, 0.999f) * 2f);
 			m_sailBottomTransform.position = Vector3.Lerp(position, position2, t);
@@ -796,7 +796,7 @@
 	{
 		if (m_nview.IsValid() && m_nview.IsOwner())
 		{
-			Gogan.LogEvent("Game", "ShipDestroyed", base.gameObject.name, 0L);
+			Gogan.LogEvent("Game", "ShipDestroyed", gameObject.name, 0L);
 		}
 		s_currentShips.Remove(this);
 	}
@@ -842,7 +842,7 @@
 
 	public float GetSpeed()
 	{
-		return Vector3.Dot(m_body.linearVelocity, base.transform.forward);
+		return Vector3.Dot(m_body.linearVelocity, transform.forward);
 	}
 
 	public Speed GetSpeedSetting()
@@ -867,20 +867,20 @@
 		{
 			return 0f;
 		}
-		return 0f - Utils.YawFromDirection(mainCamera.transform.InverseTransformDirection(base.transform.forward));
+		return 0f - Utils.YawFromDirection(mainCamera.transform.InverseTransformDirection(transform.forward));
 	}
 
 	public float GetWindAngle()
 	{
 		Vector3 windDir = EnvMan.instance.GetWindDir();
-		return 0f - Utils.YawFromDirection(base.transform.InverseTransformDirection(windDir));
+		return 0f - Utils.YawFromDirection(transform.InverseTransformDirection(windDir));
 	}
 
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.red;
-		Gizmos.DrawWireSphere(base.transform.position + base.transform.forward * m_stearForceOffset, 0.25f);
+		Gizmos.DrawWireSphere(transform.position + transform.forward * m_stearForceOffset, 0.25f);
 		Gizmos.color = Color.yellow;
-		Gizmos.DrawWireSphere(base.transform.position + base.transform.up * m_sailForceOffset, 0.25f);
+		Gizmos.DrawWireSphere(transform.position + transform.up * m_sailForceOffset, 0.25f);
 	}
 }
```
