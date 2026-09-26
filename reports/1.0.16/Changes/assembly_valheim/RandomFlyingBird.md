# `RandomFlyingBird.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/RandomFlyingBird.cs
+++ b/RandomFlyingBird.cs
@@ -101,7 +101,7 @@
 			m_flyingModel.SetActive(value: true);
 		}
 		m_idleTargetTime = UnityEngine.Random.Range(m_randomIdleTimeMin, m_randomIdleTimeMax);
-		m_spawnPoint = m_nview.GetZDO().GetVec3(ZDOVars.s_spawnPoint, base.transform.position);
+		m_spawnPoint = m_nview.GetZDO().GetVec3(ZDOVars.s_spawnPoint, transform.position);
 		if (m_nview.IsOwner())
 		{
 			m_nview.GetZDO().Set(ZDOVars.s_spawnPoint, m_spawnPoint);
@@ -142,7 +142,7 @@
 		{
 			if (flag || !m_noNoiseAtNight)
 			{
-				m_randomNoise.Create(base.transform.position, Quaternion.identity, base.transform);
+				m_randomNoise.Create(transform.position, Quaternion.identity, transform);
 			}
 			m_randomNoiseTimer = UnityEngine.Random.Range(m_randomNoiseIntervalMin, m_randomNoiseIntervalMax);
 		}
@@ -165,10 +165,10 @@
 		}
 		if (flag2)
 		{
-			Vector3 forward = base.transform.forward;
+			Vector3 forward = transform.forward;
 			forward.y = 0f;
 			forward.Normalize();
-			base.transform.rotation = Quaternion.LookRotation(forward, Vector3.up);
+			transform.rotation = Quaternion.LookRotation(forward, Vector3.up);
 			if (m_randomIdles > 0)
 			{
 				m_idleTimer += Time.fixedDeltaTime;
@@ -180,7 +180,7 @@
 				}
 			}
 			m_landedTimer += dt;
-			if (((flag || !m_noRandomFlightAtNight) && m_landedTimer > m_landDuration) || DangerNearby(base.transform.position))
+			if (((flag || !m_noRandomFlightAtNight) && m_landedTimer > m_landDuration) || DangerNearby(transform.position))
 			{
 				m_nview.GetZDO().Set(ZDOVars.s_landed, value: false);
 				RandomizeWaypoint(ground: false);
@@ -201,10 +201,10 @@
 			m_modeTimer = 0f;
 		}
 		m_anim.SetBool(s_flapping, m_flapping);
-		Vector3 vector = Vector3.Normalize(m_waypoint - base.transform.position);
+		Vector3 vector = Vector3.Normalize(m_waypoint - transform.position);
 		float num = (m_groundwp ? (m_turnRate * 4f) : m_turnRate);
-		Vector3 vector2 = Vector3.RotateTowards(base.transform.forward, vector, num * (MathF.PI / 180f) * dt, 1f);
-		float num2 = Vector3.SignedAngle(base.transform.forward, vector, Vector3.up);
+		Vector3 vector2 = Vector3.RotateTowards(transform.forward, vector, num * (MathF.PI / 180f) * dt, 1f);
+		float num2 = Vector3.SignedAngle(transform.forward, vector, Vector3.up);
 		Vector3 vector3 = Vector3.Cross(vector2, Vector3.up);
 		Vector3 up = Vector3.up;
 		if (num2 > 0f)
@@ -219,7 +219,7 @@
 		bool flag3 = false;
 		if (m_groundwp)
 		{
-			float num4 = Vector3.Distance(base.transform.position, m_waypoint);
+			float num4 = Vector3.Distance(transform.position, m_waypoint);
 			if (num4 < 5f)
 			{
 				num3 *= Mathf.Clamp(num4 / 5f, 0.2f, 1f);
@@ -230,7 +230,7 @@
 			}
 			if (num4 < 0.2f)
 			{
-				base.transform.position = m_waypoint;
+				transform.position = m_waypoint;
 				m_nview.GetZDO().Set(ZDOVars.s_landed, value: true);
 				m_landedTimer = 0f;
 				m_flapping = true;
@@ -243,14 +243,14 @@
 			RandomizeWaypoint(ground);
 		}
 		Quaternion to = Quaternion.LookRotation(vector2, up.normalized);
-		base.transform.rotation = Quaternion.RotateTowards(base.transform.rotation, to, 200f * dt);
+		transform.rotation = Quaternion.RotateTowards(transform.rotation, to, 200f * dt);
 		if (flag3)
 		{
-			base.transform.position += vector * num3 * dt;
+			transform.position += vector * num3 * dt;
 		}
 		else
 		{
-			base.transform.position += base.transform.forward * num3 * dt;
+			transform.position += transform.forward * num3 * dt;
 		}
 	}
 
```
