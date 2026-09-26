# `Projectile.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+35/-35` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Projectile.cs
+++ b/Projectile.cs
@@ -273,10 +273,10 @@
 					bool didDamage = false;
 					bool hitCharacter = false;
 					m_midFlightHitTimer = 0f;
-					DoAOE(base.transform.position, ref hitCharacter, ref didDamage);
-				}
-			}
-			Vector3 vector = base.transform.position;
+					DoAOE(transform.position, ref hitCharacter, ref didDamage);
+				}
+			}
+			Vector3 vector = transform.position;
 			if (m_haveStartPoint)
 			{
 				vector = m_startPoint;
@@ -284,29 +284,29 @@
 			m_vel += Vector3.down * (m_gravity * Time.fixedDeltaTime);
 			float num = Mathf.Pow(m_vel.magnitude, 2f) * m_drag * Time.fixedDeltaTime;
 			m_vel += num * -m_vel.normalized;
-			base.transform.position += m_vel * Time.fixedDeltaTime;
+			transform.position += m_vel * Time.fixedDeltaTime;
 			if (m_rotateVisual == 0f)
 			{
-				base.transform.rotation = Quaternion.LookRotation(m_vel);
+				transform.rotation = Quaternion.LookRotation(m_vel);
 			}
 			if (m_canHitWater)
 			{
-				float liquidLevel = Floating.GetLiquidLevel(base.transform.position);
-				if (base.transform.position.y < liquidLevel)
-				{
-					OnHit(null, base.transform.position, water: true, Vector3.up);
+				float liquidLevel = Floating.GetLiquidLevel(transform.position);
+				if (transform.position.y < liquidLevel)
+				{
+					OnHit(null, transform.position, water: true, Vector3.up);
 				}
 			}
 			m_didBounce = false;
 			if (!m_didHit)
 			{
-				Vector3 vector2 = base.transform.position - vector;
+				Vector3 vector2 = transform.position - vector;
 				if (!m_haveStartPoint)
 				{
 					vector -= vector2.normalized * (vector2.magnitude * 0.5f);
 				}
 				RaycastHit[] array = ((m_rayRadius != 0f) ? Physics.SphereCastAll(vector, m_rayRadius, vector2.normalized, vector2.magnitude, s_rayMaskSolids) : Physics.RaycastAll(vector, vector2.normalized, vector2.magnitude * 1.5f, s_rayMaskSolids));
-				Debug.DrawLine(vector, base.transform.position, (array.Length != 0) ? Color.red : Color.yellow, 5f);
+				Debug.DrawLine(vector, transform.position, (array.Length != 0) ? Color.red : Color.yellow, 5f);
 				if (array.Length != 0)
 				{
 					Array.Sort(array, (RaycastHit x, RaycastHit y) => x.distance.CompareTo(y.distance));
@@ -337,7 +337,7 @@
 				{
 					SpawnOnHit(null, null, -m_vel.normalized);
 				}
-				ZNetScene.instance.Destroy(base.gameObject);
+				ZNetScene.instance.Destroy(gameObject);
 			}
 		}
 		if (m_nview.IsValid())
@@ -357,8 +357,8 @@
 		{
 			Vector3 point = m_attachParent.transform.position - m_attachParentOffset;
 			Quaternion quaternion = m_attachParent.transform.rotation * m_attachParentOffsetRot;
-			base.transform.position = Utils.RotatePointAroundPivot(point, m_attachParent.transform.position, quaternion);
-			base.transform.localRotation = quaternion;
+			transform.position = Utils.RotatePointAroundPivot(point, m_attachParent.transform.position, quaternion);
+			transform.localRotation = quaternion;
 		}
 	}
 
@@ -377,7 +377,7 @@
 			{
 				attachPrefab = ItemStand.GetAttachGameObject(attachPrefab);
 				m_visual.gameObject.SetActive(value: false);
-				m_visual = UnityEngine.Object.Instantiate(attachPrefab, base.transform);
+				m_visual = UnityEngine.Object.Instantiate(attachPrefab, transform);
 				m_visual.transform.localPosition = Vector3.zero;
 				m_changedVisual = true;
 			}
@@ -446,19 +446,19 @@
 		if (m_doOwnerRaytest && (bool)owner)
 		{
 			m_startPoint = owner.GetCenterPoint();
-			m_startPoint.y = base.transform.position.y;
+			m_startPoint.y = transform.position.y;
 			m_haveStartPoint = true;
 		}
 		else
 		{
-			m_startPoint = base.transform.position;
+			m_startPoint = transform.position;
 		}
 		LineConnect component = GetComponent<LineConnect>();
 		if ((bool)component && (bool)owner)
 		{
 			component.SetPeer(owner.GetZDOID());
 		}
-		m_hasLeftShields = !ShieldGenerator.IsInsideShield(base.transform.position);
+		m_hasLeftShields = !ShieldGenerator.IsInsideShield(transform.position);
 	}
 
 	private void DoAOE(Vector3 hitPoint, ref bool hitCharacter, ref bool didDamage)
@@ -642,7 +642,7 @@
 			hitData.m_pushForce = m_attackForce;
 			hitData.m_backstabBonus = m_backstabBonus;
 			hitData.m_point = hitPoint;
-			hitData.m_dir = base.transform.forward;
+			hitData.m_dir = transform.forward;
 			hitData.m_statusEffectHash = m_statusEffectHash;
 			hitData.m_dodgeable = m_dodgeable;
 			hitData.m_blockable = m_blockable;
@@ -691,7 +691,7 @@
 		m_onHit?.Invoke(collider, hitPoint, water);
 		if (m_hitNoise > 0f)
 		{
-			BaseAI.DoProjectileHitNoise(base.transform.position, m_hitNoise, m_owner);
+			BaseAI.DoProjectileHitNoise(transform.position, m_hitNoise, m_owner);
 		}
 		if ((didDamage && m_owner != null) & hitCharacter)
 		{
@@ -701,7 +701,7 @@
 		if (!m_onlyStopOnTerrain | flag4)
 		{
 			m_didHit = true;
-			base.transform.position = hitPoint;
+			transform.position = hitPoint;
 			if (m_nview.IsValid())
 			{
 				m_nview.InvokeRPC("RPC_OnHit");
@@ -756,9 +756,9 @@
 			Animator componentInChildren = m_attachParent.gameObject.GetComponentInChildren<Animator>();
 			if ((object)componentInChildren != null)
 			{
-				Utils.IterateHierarchy(componentInChildren.gameObject, delegate(GameObject obj)
-				{
-					float num = Vector3.Distance(base.transform.position, obj.transform.position);
+				Utils.IterateHierarchy(componentInChildren.gameObject, (GameObject obj) =>
+				{
+					float num = Vector3.Distance(transform.position, obj.transform.position);
 					if (num < dist)
 					{
 						dist = num;
@@ -767,10 +767,10 @@
 				});
 			}
 		}
-		base.transform.position += base.transform.forward * m_attachPenetration;
-		base.transform.position += (m_attachParent.transform.position - base.transform.position) * m_attachBoneNearify;
-		m_attachParentOffset = m_attachParent.transform.position - base.transform.position;
-		m_attachParentOffsetRot = Quaternion.Inverse(m_attachParent.transform.localRotation * base.transform.localRotation);
+		transform.position += transform.forward * m_attachPenetration;
+		transform.position += (m_attachParent.transform.position - transform.position) * m_attachBoneNearify;
+		m_attachParentOffset = m_attachParent.transform.position - transform.position;
+		m_attachParentOffsetRot = Quaternion.Inverse(m_attachParent.transform.localRotation * transform.localRotation);
 	}
 
 	private void SpawnOnHit(GameObject go, Collider collider, Vector3 normal)
@@ -787,11 +787,11 @@
 				return;
 			}
 		}
-		Vector3 vector = base.transform.position + base.transform.TransformDirection(m_spawnOffset);
+		Vector3 vector = transform.position + transform.TransformDirection(m_spawnOffset);
 		Quaternion rotation = Quaternion.identity;
 		if (m_copyProjectileRotation)
 		{
-			rotation = base.transform.rotation;
+			rotation = transform.rotation;
 		}
 		if (m_spawnRandomRotation)
 		{
@@ -799,7 +799,7 @@
 		}
 		if (m_spawnFacingRotation)
 		{
-			rotation = Quaternion.Euler(0f, base.transform.rotation.eulerAngles.y, 0f);
+			rotation = Quaternion.Euler(0f, transform.rotation.eulerAngles.y, 0f);
 		}
 		if (m_spawnOnHit != null && (m_spawnOnHitChance >= 1f || UnityEngine.Random.value < m_spawnOnHitChance))
 		{
@@ -842,9 +842,9 @@
 		}
 		if (m_spawnItem != null)
 		{
-			ItemDrop.DropItem(m_spawnItem, 1, vector, base.transform.rotation);
-		}
-		if (m_randomSpawnOnHit.Count > 0 && (!m_randomSpawnSkipLava || !ZoneSystem.instance.IsLava(base.transform.position)))
+			ItemDrop.DropItem(m_spawnItem, 1, vector, transform.rotation);
+		}
+		if (m_randomSpawnOnHit.Count > 0 && (!m_randomSpawnSkipLava || !ZoneSystem.instance.IsLava(transform.position)))
 		{
 			for (int j = 0; j < (m_oneOfEachRandomSpawn ? m_randomSpawnOnHit.Count : m_randomSpawnOnHitCount); j++)
 			{
```
