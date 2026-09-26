# `GameCamera.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+20/-20` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/GameCamera.cs
+++ b/GameCamera.cs
@@ -275,19 +275,19 @@
 		if (localPlayer.IsDead() && (bool)localPlayer.GetRagdoll())
 		{
 			Vector3 averageBodyPosition = localPlayer.GetRagdoll().GetAverageBodyPosition();
-			base.transform.LookAt(averageBodyPosition);
+			transform.LookAt(averageBodyPosition);
 		}
 		else if (localPlayer.IsAttached() && localPlayer.GetAttachCameraPoint() != null)
 		{
 			Transform attachCameraPoint = localPlayer.GetAttachCameraPoint();
-			base.transform.position = attachCameraPoint.position;
-			base.transform.rotation = attachCameraPoint.rotation;
+			transform.position = attachCameraPoint.position;
+			transform.rotation = attachCameraPoint.rotation;
 		}
 		else
 		{
 			GetCameraPosition(dt, out var pos, out var rot);
-			base.transform.position = pos;
-			base.transform.rotation = rot;
+			transform.position = pos;
+			transform.rotation = rot;
 		}
 		UpdateCameraShake(dt);
 		float debugCamera(float scroll)
@@ -327,8 +327,8 @@
 		Player localPlayer = Player.m_localPlayer;
 		if (localPlayer == null)
 		{
-			pos = base.transform.position;
-			rot = base.transform.rotation;
+			pos = transform.position;
+			rot = transform.rotation;
 			return;
 		}
 		Vector3 vector = GetOffsetedEyePos();
@@ -559,10 +559,10 @@
 			else
 			{
 				int mask = LayerMask.GetMask("Default", "static_solid", "terrain", "vehicle", "character", "piece", "character_net", "viewblock");
-				if (Physics.Raycast(base.transform.position, base.transform.forward, out var hitInfo, 10000f, mask))
+				if (Physics.Raycast(transform.position, transform.forward, out var hitInfo, 10000f, mask))
 				{
 					m_freeFlyLockon = hitInfo.collider.transform;
-					m_freeFlyLockonOffset = m_freeFlyLockon.InverseTransformPoint(base.transform.position);
+					m_freeFlyLockonOffset = m_freeFlyLockon.InverseTransformPoint(transform.position);
 				}
 			}
 		}
@@ -614,7 +614,7 @@
 		{
 			vector.Normalize();
 		}
-		vector = base.transform.TransformVector(vector);
+		vector = transform.TransformVector(vector);
 		vector *= m_freeFlySpeed;
 		if (m_freeFlySmooth <= 0f)
 		{
@@ -627,11 +627,11 @@
 		if ((bool)m_freeFlyLockon)
 		{
 			m_freeFlyLockonOffset += m_freeFlyLockon.InverseTransformVector(m_freeFlyVel * dt);
-			base.transform.position = m_freeFlyLockon.TransformPoint(m_freeFlyLockonOffset);
+			transform.position = m_freeFlyLockon.TransformPoint(m_freeFlyLockonOffset);
 		}
 		else
 		{
-			base.transform.position = base.transform.position + m_freeFlyVel * dt;
+			transform.position += m_freeFlyVel * dt;
 		}
 		Quaternion quaternion = Quaternion.Euler(0f, m_freeFlyYaw, 0f) * Quaternion.Euler(m_freeFlyPitch, 0f, 0f);
 		if ((bool)m_freeFlyLockon)
@@ -647,7 +647,7 @@
 			else
 			{
 				int mask2 = LayerMask.GetMask("Default", "static_solid", "terrain", "vehicle", "character", "piece", "character_net", "viewblock");
-				if (Physics.Raycast(base.transform.position, base.transform.forward, out var hitInfo2, 10000f, mask2))
+				if (Physics.Raycast(transform.position, transform.forward, out var hitInfo2, 10000f, mask2))
 				{
 					m_freeFlyTarget = hitInfo2.collider.transform;
 					m_freeFlyTargetOffset = m_freeFlyTarget.InverseTransformPoint(hitInfo2.point);
@@ -656,15 +656,15 @@
 		}
 		if ((bool)m_freeFlyTarget)
 		{
-			quaternion = Quaternion.LookRotation((m_freeFlyTarget.TransformPoint(m_freeFlyTargetOffset) - base.transform.position).normalized, Vector3.up);
+			quaternion = Quaternion.LookRotation((m_freeFlyTarget.TransformPoint(m_freeFlyTargetOffset) - transform.position).normalized, Vector3.up);
 		}
 		if (m_freeFlySmooth <= 0f)
 		{
-			base.transform.rotation = quaternion;
+			transform.rotation = quaternion;
 			return;
 		}
-		Quaternion rotation = Utils.SmoothDamp(base.transform.rotation, quaternion, ref m_freeFlyRef, m_freeFlySmooth, 9999f, dt);
-		base.transform.rotation = rotation;
+		Quaternion rotation = Utils.SmoothDamp(transform.rotation, quaternion, ref m_freeFlyRef, m_freeFlySmooth, 9999f, dt);
+		transform.rotation = rotation;
 	}
 
 	private void UpdateCameraShake(float dt)
@@ -680,13 +680,13 @@
 		if (m_cameraShakeEnabled)
 		{
 			Quaternion quaternion = Quaternion.Euler(Mathf.Sin(m_shakeTimer) * attenuatedShakeIntensity * m_shakeMovement, Mathf.Cos(m_shakeTimer * 0.9f) * attenuatedShakeIntensity * m_shakeMovement, 0f);
-			base.transform.rotation = base.transform.rotation * quaternion;
+			transform.rotation *= quaternion;
 		}
 	}
 
 	public void AddShake(Vector3 point, float range, float strength, bool continous)
 	{
-		float num = Vector3.Distance(point, base.transform.position);
+		float num = Vector3.Distance(point, transform.position);
 		if (num > range)
 		{
 			return;
@@ -757,7 +757,7 @@
 			}
 			return m_playerPos + m_currentBaseOffset + GetCameraOffset(localPlayer);
 		}
-		return base.transform.position;
+		return transform.position;
 	}
 
 	private Vector3 GetCameraOffset(Player player)
```
