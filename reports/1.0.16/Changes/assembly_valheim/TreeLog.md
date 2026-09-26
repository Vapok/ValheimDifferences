# `TreeLog.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-17` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TreeLog.cs
+++ b/TreeLog.cs
@@ -74,7 +74,7 @@
 			}
 		}
 		Invoke("EnableDamage", 0.2f);
-		m_biome = Heightmap.FindBiome(base.transform.position);
+		m_biome = Heightmap.FindBiome(transform.position);
 		if (m_biome == Heightmap.Biome.DeepNorth)
 		{
 			if (m_snowHit == null)
@@ -91,7 +91,7 @@
 
 	private void UpdateSnow()
 	{
-		if (m_biome != Heightmap.Biome.DeepNorth || !(Vector3.Distance(m_lastSnowPos, base.transform.position) > m_snowHitDistance))
+		if (!m_nview.IsOwner() || m_biome != Heightmap.Biome.DeepNorth || !(Vector3.Distance(m_lastSnowPos, transform.position) > m_snowHitDistance))
 		{
 			return;
 		}
@@ -101,26 +101,18 @@
 		{
 			float num3 = SnowAtPoint(snowHitPosition.transform.position);
 			num = ((num3 > num) ? num3 : num);
-			if (num3 > m_minSnow)
+			if (num3 > m_minSnow && TerrainComp.ValidTCForAllAffectedHeightmaps(snowHitPosition.transform.position, m_snowHit.GetComponent<TerrainOp>().m_settings.m_paintRadius))
 			{
 				num2++;
 				UnityEngine.Object.Instantiate(m_snowHit, snowHitPosition.transform.position, snowHitPosition.transform.rotation);
 			}
 		}
-		if (num > m_minSnow && num2 >= 2)
-		{
-			float num4 = m_snowMaxWeightMultiplier / 2.1f;
-			m_body.mass = m_baseWeight * num4;
-			m_body.angularDamping = (m_baseDrag = num4);
-		}
-		else
-		{
-			m_body.mass = m_baseWeight;
-			m_body.angularDamping = m_baseDrag;
-		}
+		float num4 = m_snowMaxWeightMultiplier / 2.1f;
+		m_body.mass = Mathf.Lerp(m_baseWeight, m_baseWeight * num4, num / 2.1f);
+		m_body.angularDamping = Mathf.Lerp(m_baseDrag, m_baseDrag * num4, num / 2.1f);
 		if (num2 > 0)
 		{
-			m_lastSnowPos = base.transform.position;
+			m_lastSnowPos = transform.position;
 		}
 		float SnowAtPoint(Vector3 p)
 		{
@@ -188,10 +180,10 @@
 		if (hit.m_hitType != HitData.HitType.CinderFire)
 		{
 			ZDOID gamepadEffectsExclusiveToPlayer = (hit.GetAttacker() ? hit.GetAttacker().GetZDOID() : ZDOID.None);
-			m_hitEffect.Create(hit.m_point, Quaternion.identity, base.transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
+			m_hitEffect.Create(hit.m_point, Quaternion.identity, transform, 1f, -1, gamepadEffectsExclusiveToPlayer);
 			if (m_hitNoise > 0f)
 			{
-				Player closestPlayer = Player.GetClosestPlayer(base.transform.position, 10f);
+				Player closestPlayer = Player.GetClosestPlayer(transform.position, 10f);
 				if ((bool)closestPlayer)
 				{
 					closestPlayer.AddNoise(m_hitNoise);
```
