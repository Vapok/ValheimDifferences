# `Fish.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+24/-24` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Fish.cs
+++ b/Fish.cs
@@ -201,7 +201,7 @@
 			itemDrop.m_onDrop = (Action<ItemDrop>)Delegate.Combine(itemDrop.m_onDrop, new Action<ItemDrop>(onDrop));
 			if (m_pickupItem == null)
 			{
-				m_pickupItem = base.gameObject;
+				m_pickupItem = gameObject;
 			}
 		}
 		m_waterWaveCount = UnityEngine.Random.Range(0, 1);
@@ -213,7 +213,7 @@
 
 	private void Start()
 	{
-		m_spawnPoint = m_nview.GetZDO().GetVec3(ZDOVars.s_spawnPoint, base.transform.position);
+		m_spawnPoint = m_nview.GetZDO().GetVec3(ZDOVars.s_spawnPoint, transform.position);
 		if (m_nview.IsOwner())
 		{
 			m_nview.GetZDO().Set(ZDOVars.s_spawnPoint, m_spawnPoint);
@@ -226,8 +226,8 @@
 		}
 		if (m_waterVolume != null)
 		{
-			m_waterDepth = m_waterVolume.Depth(base.transform.position);
-			m_waterWave = m_waterVolume.CalcWave(base.transform.position, m_waterDepth, s_wrappedTimeSeconds, 1f, 1f - (float)WorldGenerator.DeepNorthWaveFade(base.transform.position.x, base.transform.position.z));
+			m_waterDepth = m_waterVolume.Depth(transform.position);
+			m_waterWave = m_waterVolume.CalcWave(transform.position, m_waterDepth, s_wrappedTimeSeconds, 1f, 1f - (float)WorldGenerator.DeepNorthWaveFade(transform.position.x, transform.position.z));
 		}
 	}
 
@@ -344,12 +344,12 @@
 		{
 			return null;
 		}
-		return base.transform;
+		return transform;
 	}
 
 	public bool IsOutOfWater()
 	{
-		return m_inWater < base.transform.position.y - m_height;
+		return m_inWater < transform.position.y - m_height;
 	}
 
 	public void CustomFixedUpdate(float fixedDeltaTime)
@@ -379,7 +379,7 @@
 				m_isJumping = false;
 			}
 		}
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		bool flag = IsOutOfWater();
 		if (m_waterVolume != null)
 		{
@@ -400,7 +400,7 @@
 		}
 		if (!flag && UnityEngine.Random.value > 0.975f && m_nview.GetZDO().GetInt(ZDOVars.s_hooked) == 1 && m_nview.GetZDO().GetFloat(ZDOVars.s_escape) > 0f)
 		{
-			m_jumpEffects.Create(position, Quaternion.identity, base.transform);
+			m_jumpEffects.Create(position, Quaternion.identity, transform);
 		}
 		if (!m_nview.IsOwner())
 		{
@@ -531,9 +531,9 @@
 
 	private void Stop(float dt)
 	{
-		if (!(m_inWater < base.transform.position.y + m_height))
-		{
-			Vector3 forward = base.transform.forward;
+		if (!(m_inWater < transform.position.y + m_height))
+		{
+			Vector3 forward = transform.forward;
 			forward.y = 0f;
 			forward.Normalize();
 			Quaternion to = Quaternion.LookRotation(forward, Vector3.up);
@@ -560,7 +560,7 @@
 			num *= m_avoidSpeedScale;
 		}
 		Quaternion to = Quaternion.LookRotation(vector, Vector3.up);
-		Quaternion rotation = Quaternion.RotateTowards(base.transform.rotation, to, num * dt);
+		Quaternion rotation = Quaternion.RotateTowards(transform.rotation, to, num * dt);
 		if (!m_isJumping || !(m_body.linearVelocity.y > 0f))
 		{
 			if (!m_isJumping)
@@ -572,18 +572,18 @@
 			{
 				num2 *= m_avoidSpeedScale;
 			}
-			if (avoidLand && GetPointDepth(base.transform.position + base.transform.forward) < m_minDepth)
+			if (avoidLand && GetPointDepth(transform.position + transform.forward) < m_minDepth)
 			{
 				num2 = 0f;
 			}
-			if (fast && Vector3.Dot(dir, base.transform.forward) < 0f)
+			if (fast && Vector3.Dot(dir, transform.forward) < 0f)
 			{
 				num2 = 0f;
 			}
-			Vector3 forward = base.transform.forward;
+			Vector3 forward = transform.forward;
 			forward.y = dir.y;
 			Vector3 vector2 = forward * num2 - m_body.linearVelocity;
-			if (m_inWater < base.transform.position.y + m_height && vector2.y > 0f)
+			if (m_inWater < transform.position.y + m_height && vector2.y > 0f)
 			{
 				vector2.y = 0f;
 			}
@@ -595,7 +595,7 @@
 	{
 		foreach (FishingFloat allInstance in FishingFloat.GetAllInstances())
 		{
-			if (allInstance.IsInWater() && !(Vector3.Distance(base.transform.position, allInstance.transform.position) > allInstance.m_range) && !(allInstance.GetCatch() != null))
+			if (allInstance.IsInWater() && !(Vector3.Distance(transform.position, allInstance.transform.position) > allInstance.m_range) && !(allInstance.GetCatch() != null))
 			{
 				float baseHookChance = m_baseHookChance;
 				if (UnityEngine.Random.value < baseHookChance)
@@ -643,7 +643,7 @@
 		{
 			return false;
 		}
-		Vector3 p = (m_waypoint + base.transform.position) * 0.5f;
+		Vector3 p = (m_waypoint + transform.position) * 0.5f;
 		if (GetPointDepth(p) < m_minDepth)
 		{
 			return false;
@@ -683,7 +683,7 @@
 
 	private bool DangerNearby()
 	{
-		return Player.GetPlayerNoiseRange(base.transform.position) != null;
+		return Player.GetPlayerNoiseRange(transform.position) != null;
 	}
 
 	public ZDOID GetZDOID()
@@ -694,7 +694,7 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.blue;
-		Gizmos.DrawWireCube(base.transform.position + Vector3.up * m_height, new Vector3(1f, 0.02f, 1f));
+		Gizmos.DrawWireCube(transform.position + Vector3.up * m_height, new Vector3(1f, 0.02f, 1f));
 	}
 
 	private void OnCollisionEnter(Collision collision)
@@ -758,15 +758,15 @@
 				m_jumpedFromLand = true;
 				m_JumpHeightStrength *= m_jumpOnLandDecay;
 				float jumpOnLandRotation = m_jumpOnLandRotation;
-				m_body.AddForce(new Vector3(0f, m_JumpHeightStrength * m_jumpHeightLand * base.transform.localScale.y, 0f), ForceMode.Impulse);
+				m_body.AddForce(new Vector3(0f, m_JumpHeightStrength * m_jumpHeightLand * transform.localScale.y, 0f), ForceMode.Impulse);
 				m_body.AddTorque(UnityEngine.Random.Range(0f - jumpOnLandRotation, jumpOnLandRotation), UnityEngine.Random.Range(0f - jumpOnLandRotation, jumpOnLandRotation), UnityEngine.Random.Range(0f - jumpOnLandRotation, jumpOnLandRotation), ForceMode.Impulse);
 			}
 			else
 			{
 				m_jumpedFromLand = false;
-				m_jumpEffects.Create(base.transform.position, Quaternion.identity);
-				m_body.AddForce(new Vector3(0f, m_jumpHeight * base.transform.localScale.y, 0f), ForceMode.Impulse);
-				m_body.AddForce(base.transform.forward * (m_jumpForwardStrength * base.transform.localScale.y), ForceMode.Impulse);
+				m_jumpEffects.Create(transform.position, Quaternion.identity);
+				m_body.AddForce(new Vector3(0f, m_jumpHeight * transform.localScale.y, 0f), ForceMode.Impulse);
+				m_body.AddForce(transform.forward * (m_jumpForwardStrength * transform.localScale.y), ForceMode.Impulse);
 			}
 		}
 	}
```
