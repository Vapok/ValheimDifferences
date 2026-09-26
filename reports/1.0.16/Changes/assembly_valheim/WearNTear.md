# `WearNTear.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+48/-48` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/WearNTear.cs
+++ b/WearNTear.cs
@@ -335,7 +335,7 @@
 
 	private void Start()
 	{
-		m_connectedHeightMap = Heightmap.FindHeightmap(base.transform.position);
+		m_connectedHeightMap = Heightmap.FindHeightmap(transform.position);
 		if (m_connectedHeightMap != null)
 		{
 			m_connectedHeightMap.m_clearConnectedWearNTearCache += ClearCachedSupport;
@@ -376,7 +376,7 @@
 		if (m_ashMaterialValue != v)
 		{
 			m_ashMaterialValue = v;
-			MaterialMan.instance.SetValue(base.gameObject, s_AshlandsDamageShaderID, v);
+			MaterialMan.instance.SetValue(gameObject, s_AshlandsDamageShaderID, v);
 		}
 	}
 
@@ -467,16 +467,16 @@
 			V = Mathf.Lerp(1.2f, 0.9f, supportColorValue);
 			color = Color.HSVToRGB(H, S, V);
 		}
-		MaterialMan.instance.SetValue(base.gameObject, ShaderProps._EmissionColor, color * 0.4f);
-		MaterialMan.instance.SetValue(base.gameObject, ShaderProps._Color, color);
+		MaterialMan.instance.SetValue(gameObject, ShaderProps._EmissionColor, color * 0.4f);
+		MaterialMan.instance.SetValue(gameObject, ShaderProps._Color, color);
 		CancelInvoke("ResetHighlight");
 		Invoke("ResetHighlight", 0.2f);
 	}
 
 	private void ResetHighlight()
 	{
-		MaterialMan.instance.ResetValue(base.gameObject, ShaderProps._Color);
-		MaterialMan.instance.ResetValue(base.gameObject, ShaderProps._EmissionColor);
+		MaterialMan.instance.ResetValue(gameObject, ShaderProps._Color);
+		MaterialMan.instance.ResetValue(gameObject, ShaderProps._EmissionColor);
 	}
 
 	private void SetupColliders()
@@ -488,7 +488,7 @@
 		{
 			if (!collider.isTrigger && !(collider.attachedRigidbody != null))
 			{
-				BoundData item = default(BoundData);
+				BoundData item = default;
 				if (collider is BoxCollider)
 				{
 					BoxCollider boxCollider = collider as BoxCollider;
@@ -528,7 +528,7 @@
 		}
 		if (m_nview.IsOwner() && ShouldUpdate(time))
 		{
-			if (ZNetScene.instance.OutsideActiveArea(base.transform.position))
+			if (ZNetScene.instance.OutsideActiveArea(transform.position))
 			{
 				float maxSupport = GetMaxSupport();
 				if (!m_support.Equals(maxSupport))
@@ -537,7 +537,7 @@
 				}
 				return;
 			}
-			bool flag = ShieldGenerator.IsInsideShieldCached(base.transform.position, ref m_shieldChangeID);
+			bool flag = ShieldGenerator.IsInsideShieldCached(transform.position, ref m_shieldChangeID);
 			float num = 0f;
 			m_rainWet = !flag && !m_haveRoof && m_noRoofWear && EnvMan.IsWet();
 			if ((bool)m_wet)
@@ -573,7 +573,7 @@
 			}
 			if (!string.IsNullOrEmpty(m_requiredPersistentEvent))
 			{
-				PersistentEventSystem.PersistentEvent activeEvent = PersistentEventSystem.instance.GetActiveEvent(base.transform.position);
+				PersistentEventSystem.PersistentEvent activeEvent = PersistentEventSystem.instance.GetActiveEvent(transform.position);
 				if (m_takeDamageIfInsideEvent && activeEvent != null && activeEvent.internalName == m_requiredPersistentEvent)
 				{
 					num += m_eventDamage + UnityEngine.Random.Range(0f - m_eventDamageDeviation, m_eventDamageDeviation);
@@ -620,7 +620,7 @@
 							if (ZNet.instance.GetTimeSeconds() >= (double)m_snowDamageTimer)
 							{
 								m_snowDamageTimer = (float)ZNet.instance.GetTimeSeconds() + UnityEngine.Random.Range(Game.instance.m_snowDamageEffectIntervalRange.x, Game.instance.m_snowDamageEffectIntervalRange.y);
-								Game.instance.m_snowDamageEffect.Create(base.transform.position, Quaternion.identity, base.transform);
+								Game.instance.m_snowDamageEffect.Create(transform.position, Quaternion.identity, transform);
 							}
 						}
 					}
@@ -651,7 +651,7 @@
 				}
 				if (!m_staticPosition)
 				{
-					m_lavaValue = m_heightmap.GetLava(base.transform.position);
+					m_lavaValue = m_heightmap.GetLava(transform.position);
 				}
 				if (m_lavaValue > 0.2f && m_groundDist < 1.5f && !m_ashDamageImmune)
 				{
@@ -702,13 +702,13 @@
 		{
 			return;
 		}
-		Vector3 p = base.transform.position;
+		Vector3 p = transform.position;
 		ZoneSystem.instance.GetGroundData(ref p, out var _, out var _, out var _, out m_heightmap);
 		if (!(m_heightmap != null))
 		{
 			return;
 		}
-		m_biome = m_heightmap.GetBiome(base.transform.position);
+		m_biome = m_heightmap.GetBiome(transform.position);
 		float num = 9999f;
 		foreach (Renderer renderer in m_renderers)
 		{
@@ -724,13 +724,13 @@
 		m_groundDist = num - p.y;
 		if (m_staticPosition)
 		{
-			m_lavaValue = m_heightmap.GetLava(base.transform.position);
+			m_lavaValue = m_heightmap.GetLava(transform.position);
 		}
 	}
 
 	public bool CanHaveSnow(bool forceCover = false)
 	{
-		return CanHaveSnow(ShieldGenerator.IsInsideShieldCached(base.transform.position, ref m_shieldChangeID), forceCover);
+		return CanHaveSnow(ShieldGenerator.IsInsideShieldCached(transform.position, ref m_shieldChangeID), forceCover);
 	}
 
 	public bool CanHaveSnow(bool isShielded, bool forceCover = false)
@@ -786,14 +786,14 @@
 			}
 			if (m_snowBuildup > 0.25f)
 			{
-				MaterialMan.instance.SetValue(base.gameObject, s_snowLevel, Mathf.Clamp01(Utils.Remap(m_snowBuildup, 0.25f, 1f, 0f, 1f)));
+				MaterialMan.instance.SetValue(gameObject, s_snowLevel, Mathf.Clamp01(Utils.Remap(m_snowBuildup, 0.25f, 1f, 0f, 1f)));
 			}
 		}
 	}
 
 	private Vector3 GetCOM()
 	{
-		return base.transform.position + base.transform.rotation * m_comOffset;
+		return transform.position + transform.rotation * m_comOffset;
 	}
 
 	public bool IsWet()
@@ -907,10 +907,10 @@
 				WearNTear componentInParent3 = collider3.GetComponentInParent<WearNTear>();
 				if (componentInParent3 == null)
 				{
-					bool num5 = !m_support.Equals(maxSupport);
+					bool flag2 = !m_support.Equals(maxSupport);
 					m_support = maxSupport;
 					ClearCachedSupport();
-					if (num5)
+					if (flag2)
 					{
 						m_nview.GetZDO().Set(ZDOVars.s_support, m_support);
 					}
@@ -920,14 +920,14 @@
 				{
 					continue;
 				}
-				float num6 = Vector3.Distance(cOM, componentInParent3.GetCOM()) + 0.1f;
-				float num7 = Vector3.Distance(cOM, componentInParent3.transform.position) + 0.1f;
-				if (num7 < num6 && !m_forceCorrectCOMCalculation)
-				{
-					num6 = num7;
+				float num5 = Vector3.Distance(cOM, componentInParent3.GetCOM()) + 0.1f;
+				float num6 = Vector3.Distance(cOM, componentInParent3.transform.position) + 0.1f;
+				if (num6 < num5 && !m_forceCorrectCOMCalculation)
+				{
+					num5 = num6;
 				}
 				float support2 = componentInParent3.GetSupport();
-				num3 = Mathf.Max(num3, support2 - horizontalLoss * num6 * support2);
+				num3 = Mathf.Max(num3, support2 - horizontalLoss * num5 * support2);
 				Vector3 vector = FindSupportPoint(cOM, componentInParent3, collider3);
 				if (vector.y < cOM.y + 0.05f)
 				{
@@ -935,11 +935,11 @@
 					if (normalized.y < 0f)
 					{
 						float t = Mathf.Acos(1f - Mathf.Abs(normalized.y)) / (MathF.PI / 2f);
-						float num8 = Mathf.Lerp(horizontalLoss, verticalLoss, t);
-						float b = support2 - num8 * num6 * support2;
+						float num7 = Mathf.Lerp(horizontalLoss, verticalLoss, t);
+						float b = support2 - num7 * num5 * support2;
 						num3 = Mathf.Max(num3, b);
 					}
-					float item = support2 - verticalLoss * num6 * support2;
+					float item = support2 - verticalLoss * num5 * support2;
 					s_tempSupportPoints.Add(vector);
 					s_tempSupportPointValues.Add(item);
 					m_supportColliders.Add(collider3);
@@ -950,9 +950,9 @@
 		}
 		if (flag)
 		{
-			bool num9 = !m_support.Equals(maxSupport);
+			bool flag3 = !m_support.Equals(maxSupport);
 			m_support = maxSupport;
-			if (num9)
+			if (flag3)
 			{
 				m_nview.GetZDO().Set(ZDOVars.s_support, m_support);
 			}
@@ -967,14 +967,14 @@
 				vector2.y = 0f;
 				for (int m = l + 1; m < count2; m++)
 				{
-					float num10 = (s_tempSupportPointValues[l] + s_tempSupportPointValues[m]) * 0.5f;
-					if (!(num10 <= num3))
+					float num8 = (s_tempSupportPointValues[l] + s_tempSupportPointValues[m]) * 0.5f;
+					if (!(num8 <= num3))
 					{
 						Vector3 to = s_tempSupportPoints[m] - cOM;
 						to.y = 0f;
 						if (Vector3.Angle(vector2, to) >= 100f)
 						{
-							num3 = num10;
+							num3 = num8;
 						}
 					}
 				}
@@ -1013,7 +1013,7 @@
 
 	private bool IsUnderWater()
 	{
-		return Floating.IsUnderWater(base.transform.position, ref m_previousWaterVolume);
+		return Floating.IsUnderWater(transform.position, ref m_previousWaterVolume);
 	}
 
 	public void UpdateCover(float dt)
@@ -1039,7 +1039,7 @@
 		{
 			return true;
 		}
-		return RoofCheck(base.transform, base.transform.position, out m_roof, m_roofCheckOffset);
+		return RoofCheck(transform, transform.position, out m_roof, m_roofCheckOffset);
 	}
 
 	public static bool RoofCheck(Transform obj, Vector3 position, out GameObject roofObject, float heightOffset = 0f)
@@ -1064,11 +1064,11 @@
 		{
 			return true;
 		}
-		int num = Physics.SphereCastNonAlloc(base.transform.position, 0.1f, Vector3.up, s_raycastHits, 100f, s_rayMask);
+		int num = Physics.SphereCastNonAlloc(transform.position, 0.1f, Vector3.up, s_raycastHits, 100f, s_rayMask);
 		for (int i = 0; i < num; i++)
 		{
 			RaycastHit raycastHit = s_raycastHits[i];
-			if (raycastHit.collider.gameObject != base.gameObject && (raycastHit.collider.transform.parent == null || raycastHit.collider.transform.parent.gameObject != base.gameObject))
+			if (raycastHit.collider.gameObject != gameObject && (raycastHit.collider.transform.parent == null || raycastHit.collider.transform.parent.gameObject != gameObject))
 			{
 				m_ashroof = raycastHit.collider.gameObject;
 				return true;
@@ -1115,7 +1115,7 @@
 		{
 			if (triggerEffects && !m_worn.activeSelf)
 			{
-				m_switchEffect.Create(base.transform.position, base.transform.rotation, base.transform);
+				m_switchEffect.Create(transform.position, transform.rotation, transform);
 			}
 			if (m_new != m_worn)
 			{
@@ -1131,7 +1131,7 @@
 		{
 			if (triggerEffects && !m_broken.activeSelf)
 			{
-				m_switchEffect.Create(base.transform.position, base.transform.rotation, base.transform);
+				m_switchEffect.Create(transform.position, transform.rotation, transform);
 			}
 			if (m_new != m_broken)
 			{
@@ -1209,7 +1209,7 @@
 			if ((bool)attacker)
 			{
 				bool destroyed = totalDamage >= m_nview.GetZDO().GetFloat(ZDOVars.s_health, m_health);
-				PrivateArea.OnObjectDamaged(base.transform.position, attacker, destroyed);
+				PrivateArea.OnObjectDamaged(transform.position, attacker, destroyed);
 			}
 		}
 		if (!hit.CheckToolTier(m_minToolTier, alwaysAllowTierZero: true))
@@ -1221,10 +1221,10 @@
 		if (hit.m_hitType != HitData.HitType.CinderFire && hit.m_hitType != HitData.HitType.AshlandsOcean)
 		{
 			ZDOID gamepadEffectsExclusiveToPlayer = (((object)hit.GetAttacker() != null) ? hit.GetAttacker().GetZDOID() : ZDOID.None);
-			m_hitEffect.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
+			m_hitEffect.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
 			if (hit.GetTotalPhysicalDamage() > 0f)
 			{
-				m_hitEffect.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
+				m_hitEffect.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
 			}
 		}
 		if (m_hitNoise > 0f && hit.m_hitType != HitData.HitType.CinderFire)
@@ -1256,7 +1256,7 @@
 		m_nview.GetZDO().Set(ZDOVars.s_health, num);
 		if (Terminal.m_showTests && Terminal.m_testList.ContainsKey("damage"))
 		{
-			Terminal.Log(string.Format("Damage WNT: {0} took {1} damage from {2}", base.gameObject.name, damage, (hitData == null) ? ((object)"UNKNOWN") : ((object)hitData)));
+			Terminal.Log(string.Format("Damage WNT: {0} took {1} damage from {2}", gameObject.name, damage, (hitData == null) ? ((object)"UNKNOWN") : ((object)hitData)));
 		}
 		if (num <= 0f)
 		{
@@ -1307,7 +1307,7 @@
 		}
 		if (m_destroyNoise > 0f && (hitData == null || hitData.m_hitType != HitData.HitType.CinderFire))
 		{
-			Player closestPlayer = Player.GetClosestPlayer(base.transform.position, 10f);
+			Player closestPlayer = Player.GetClosestPlayer(transform.position, 10f);
 			if ((bool)closestPlayer)
 			{
 				closestPlayer.AddNoise(m_destroyNoise);
@@ -1318,12 +1318,12 @@
 		{
 			gamepadEffectsExclusiveToPlayer = hitData.GetAttacker().GetZDOID();
 		}
-		m_destroyedEffect.Create(base.transform.position, base.transform.rotation, base.transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
+		m_destroyedEffect.Create(transform.position, transform.rotation, transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
 		if (m_autoCreateFragments)
 		{
 			m_nview.InvokeRPC(ZNetView.Everybody, "RPC_CreateFragments");
 		}
-		ZNetScene.instance.Destroy(base.gameObject);
+		ZNetScene.instance.Destroy(gameObject);
 	}
 
 	private void RPC_CreateFragments(long peer)
@@ -1340,7 +1340,7 @@
 		}
 		else
 		{
-			Destructible.CreateFragments(base.gameObject);
+			Destructible.CreateFragments(gameObject);
 		}
 	}
 
```
