# `Fireplace.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+26/-26` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Fireplace.cs
+++ b/Fireplace.cs
@@ -114,8 +114,8 @@
 
 	public void Awake()
 	{
-		m_nview = base.gameObject.GetComponent<ZNetView>();
-		m_piece = base.gameObject.GetComponent<Piece>();
+		m_nview = gameObject.GetComponent<ZNetView>();
+		m_piece = gameObject.GetComponent<Piece>();
 		if (m_nview.GetZDO() == null)
 		{
 			return;
@@ -129,10 +129,10 @@
 			m_nview.GetZDO().Set(ZDOVars.s_fuel, m_startFuel);
 			if (m_startFuel > 0f)
 			{
-				m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation);
-			}
-		}
-		Vector3 p = (m_enabledObject ? m_enabledObject.transform.position : base.transform.position);
+				m_fuelAddedEffects.Create(transform.position, transform.rotation);
+			}
+		}
+		Vector3 p = (m_enabledObject ? m_enabledObject.transform.position : transform.position);
 		p.y -= 15f;
 		m_checkWaterLevel = Floating.IsUnderWater(p, ref m_previousWaterVolume);
 		m_nview.Register("RPC_AddFuel", RPC_AddFuel);
@@ -145,7 +145,7 @@
 		{
 			InvokeRepeating("UpdateIgnite", m_igniteInterval, m_igniteInterval);
 		}
-		if ((bool)m_snowMelter && Heightmap.FindBiome(base.transform.position) == Heightmap.Biome.DeepNorth)
+		if ((bool)m_snowMelter && Heightmap.FindBiome(transform.position) == Heightmap.Biome.DeepNorth)
 		{
 			UpdateSnowMelt();
 			InvokeRepeating("UpdateSnowMelt", UnityEngine.Random.Range(m_snowMelterInterval, m_snowMelterInterval * 2f), m_snowMelterInterval);
@@ -214,11 +214,11 @@
 		if (!m_disableCoverCheck)
 		{
 			RaycastHit hitInfo;
-			if (Heightmap.GetHeight(base.transform.position, out var height) && height > base.transform.position.y + m_checkTerrainOffset)
+			if (Heightmap.GetHeight(transform.position, out var height) && height > transform.position.y + m_checkTerrainOffset)
 			{
 				m_blocked = true;
 			}
-			else if (Physics.Raycast(base.transform.position + Vector3.up * m_coverCheckOffset, Vector3.up, out hitInfo, 0.5f, m_solidRayMask))
+			else if (Physics.Raycast(transform.position + Vector3.up * m_coverCheckOffset, Vector3.up, out hitInfo, 0.5f, m_solidRayMask))
 			{
 				m_blocked = true;
 			}
@@ -236,7 +236,7 @@
 		bool flag2 = EnvMan.IsWet();
 		if (flag | flag2)
 		{
-			Cover.GetCoverForPoint(base.transform.position + Vector3.up * m_coverCheckOffset, out var coverPercentage, out var underRoof);
+			Cover.GetCoverForPoint(transform.position + Vector3.up * m_coverCheckOffset, out var coverPercentage, out var underRoof);
 			if (flag && coverPercentage < 0.7f)
 			{
 				m_wet = true;
@@ -327,9 +327,9 @@
 
 	private void UpdateSnowMelt()
 	{
-		if (IsBurning())
-		{
-			UnityEngine.Object.Instantiate(m_snowMelter, base.transform.position, base.transform.rotation);
+		if (IsBurning() && m_nview.IsOwner() && TerrainComp.ValidTCForAllAffectedHeightmaps(transform.position, m_snowMelter.GetComponent<TerrainOp>().m_settings.m_paintRadius))
+		{
+			UnityEngine.Object.Instantiate(m_snowMelter, transform.position, transform.rotation);
 		}
 	}
 
@@ -458,8 +458,8 @@
 				float x = UnityEngine.Random.Range(0f - m_fireworksMaxRandomAngle, m_fireworksMaxRandomAngle);
 				float z = UnityEngine.Random.Range(0f - m_fireworksMaxRandomAngle, m_fireworksMaxRandomAngle);
 				Quaternion baseRot = Quaternion.Euler(x, 0f, z);
-				m_fireworkItemList[i].m_fireworksEffects.Create(base.transform.position, baseRot);
-				m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation);
+				m_fireworkItemList[i].m_fireworksEffects.Create(transform.position, baseRot);
+				m_fuelAddedEffects.Create(transform.position, transform.rotation);
 				return true;
 			}
 		}
@@ -477,7 +477,7 @@
 				num++;
 				num = Mathf.Clamp(num, 0f, m_maxFuel);
 				m_nview.GetZDO().Set(ZDOVars.s_fuel, num);
-				m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation);
+				m_fuelAddedEffects.Create(transform.position, transform.rotation);
 				UpdateState();
 			}
 		}
@@ -489,7 +489,7 @@
 		{
 			bool flag = m_nview.GetZDO().GetInt(ZDOVars.s_state, 1) == 1;
 			m_nview.GetZDO().Set(ZDOVars.s_state, (!flag) ? 1 : 2);
-			m_toggleOnEffects.Create(base.transform.position, Quaternion.identity, null, 1f, (!flag) ? 1 : 2);
+			m_toggleOnEffects.Create(transform.position, Quaternion.identity, null, 1f, (!flag) ? 1 : 2);
 		}
 		UpdateState();
 	}
@@ -501,7 +501,7 @@
 			float num = m_nview.GetZDO().GetFloat(ZDOVars.s_fuel);
 			num = Mathf.Clamp(num + amount, 0f, m_maxFuel);
 			m_nview.GetZDO().Set(ZDOVars.s_fuel, num);
-			m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation);
+			m_fuelAddedEffects.Create(transform.position, transform.rotation);
 			UpdateState();
 		}
 	}
@@ -524,7 +524,7 @@
 		if (m_nview.IsOwner())
 		{
 			m_nview.GetZDO().Set(ZDOVars.s_fuel, fuel);
-			m_fuelAddedEffects.Create(base.transform.position, base.transform.rotation);
+			m_fuelAddedEffects.Create(transform.position, transform.rotation);
 			UpdateState();
 		}
 	}
@@ -544,7 +544,7 @@
 		{
 			return false;
 		}
-		if (m_checkWaterLevel && Floating.IsUnderWater(m_enabledObject ? m_enabledObject.transform.position : base.transform.position, ref m_previousWaterVolume))
+		if (m_checkWaterLevel && Floating.IsUnderWater(m_enabledObject ? m_enabledObject.transform.position : transform.position, ref m_previousWaterVolume))
 		{
 			return false;
 		}
@@ -558,11 +558,11 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.white;
-		Gizmos.DrawWireSphere(base.transform.position + Vector3.up * m_coverCheckOffset, 0.5f);
+		Gizmos.DrawWireSphere(transform.position + Vector3.up * m_coverCheckOffset, 0.5f);
 		Gizmos.color = Color.yellow;
-		Gizmos.DrawWireCube(base.transform.position + Vector3.up * m_checkTerrainOffset, new Vector3(1f, 0.01f, 1f));
+		Gizmos.DrawWireCube(transform.position + Vector3.up * m_checkTerrainOffset, new Vector3(1f, 0.01f, 1f));
 		Gizmos.color = Color.red;
-		Utils.DrawGizmoCapsule(base.transform.position + m_igniteCapsuleStart, base.transform.position + m_igniteCapsuleEnd, m_igniteCapsuleRadius);
+		Utils.DrawGizmoCapsule(transform.position + m_igniteCapsuleStart, transform.position + m_igniteCapsuleEnd, m_igniteCapsuleRadius);
 	}
 
 	private void UpdateIgnite()
@@ -571,11 +571,11 @@
 		{
 			return;
 		}
-		int num = Physics.OverlapCapsuleNonAlloc(base.transform.position + m_igniteCapsuleStart, base.transform.position + m_igniteCapsuleEnd, m_igniteCapsuleRadius, s_tempColliders);
+		int num = Physics.OverlapCapsuleNonAlloc(transform.position + m_igniteCapsuleStart, transform.position + m_igniteCapsuleEnd, m_igniteCapsuleRadius, s_tempColliders);
 		for (int i = 0; i < num; i++)
 		{
 			Collider collider = s_tempColliders[i];
-			if (!(collider.gameObject == base.gameObject) && (!(collider.transform.parent != null) || !(collider.transform.parent.gameObject == base.gameObject)) && !collider.isTrigger && UnityEngine.Random.Range(0f, 1f) <= m_igniteChance && Cinder.CanBurn(collider, collider.transform.position, out var _))
+			if (!(collider.gameObject == gameObject) && (!(collider.transform.parent != null) || !(collider.transform.parent.gameObject == gameObject)) && !collider.isTrigger && UnityEngine.Random.Range(0f, 1f) <= m_igniteChance && Cinder.CanBurn(collider, collider.transform.position, out var _))
 			{
 				UnityEngine.Object.Instantiate(m_firePrefab, collider.transform.position + Utils.RandomVector3(-0.1f, 0.1f), Quaternion.identity).GetComponent<CinderSpawner>()?.Setup(m_igniteSpread, collider.gameObject);
 			}
@@ -624,7 +624,7 @@
 
 	public bool CanIgnite()
 	{
-		return CinderSpawner.CanSpawnCinder(base.transform, ref m_biome);
+		return CinderSpawner.CanSpawnCinder(transform, ref m_biome);
 	}
 
 	public float GetHoverOffset()
```
