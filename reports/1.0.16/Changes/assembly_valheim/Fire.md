# `Fire.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-9` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Fire.cs
+++ b/Fire.cs
@@ -98,7 +98,7 @@
 			s_smokeRayMask = LayerMask.GetMask("smoke");
 		}
 		InvokeRepeating("Dot", m_dotInterval, m_dotInterval);
-		if ((bool)m_terrainHitSpawn && (m_terrainHitBiomes == Heightmap.Biome.All || m_terrainHitBiomes.HasFlag(WorldGenerator.instance.GetBiome(base.transform.position))))
+		if ((bool)m_terrainHitSpawn && (m_terrainHitBiomes == Heightmap.Biome.All || m_terrainHitBiomes.HasFlag(WorldGenerator.instance.GetBiome(transform.position))))
 		{
 			Invoke("HitTerrain", m_terrainHitDelay);
 		}
@@ -118,7 +118,7 @@
 			return;
 		}
 		m_destructibles.Clear();
-		int num = Physics.OverlapSphereNonAlloc(base.transform.position, m_dotRadius, m_colliders, s_dotMask);
+		int num = Physics.OverlapSphereNonAlloc(transform.position, m_dotRadius, m_colliders, s_dotMask);
 		for (int i = 0; i < num; i++)
 		{
 			GameObject gameObject = Projectile.FindHitObject(m_colliders[i]);
@@ -152,7 +152,7 @@
 		hitData.m_damage.m_fire = m_fireDamage;
 		hitData.m_damage.m_chop = m_chopDamage;
 		hitData.m_toolTier = m_toolTier;
-		hitData.m_point = (base.transform.position + collider.bounds.center) * 0.5f;
+		hitData.m_point = (transform.position + collider.bounds.center) * 0.5f;
 		hitData.m_dodgeable = false;
 		hitData.m_blockable = false;
 		hitData.m_hitType = HitData.HitType.CinderFire;
@@ -162,7 +162,7 @@
 
 	private void HitTerrain()
 	{
-		if (Physics.Raycast(base.transform.position, Vector3.down, out var hitInfo, m_terrainMaxDist, s_terrainMask))
+		if (Physics.Raycast(transform.position, Vector3.down, out var hitInfo, m_terrainMaxDist, s_terrainMask))
 		{
 			Heightmap component = hitInfo.collider.GetComponent<Heightmap>();
 			if ((object)component != null && !component.IsLava(hitInfo.point) && ((m_terrainCheckCultivated && !component.IsCultivated(hitInfo.point)) || (m_terrainCheckCleared && !component.IsCleared(hitInfo.point)) || (!m_terrainCheckCleared && !m_terrainCheckCultivated)))
@@ -180,15 +180,15 @@
 		}
 		if (!m_roof)
 		{
-			WearNTear.RoofCheck(base.transform, base.transform.position, out m_roof);
+			WearNTear.RoofCheck(transform, transform.position, out m_roof);
 		}
 		if (!m_roof && EnvMan.IsWet())
 		{
-			ZNetScene.instance.Destroy(base.gameObject);
+			ZNetScene.instance.Destroy(gameObject);
 		}
 		if ((bool)m_roof)
 		{
-			m_smokeHits = Physics.OverlapSphereNonAlloc(base.transform.position + Vector3.up * m_smokeOxygenCheckHeight, m_smokeOxygenCheckRadius, s_hits, s_smokeRayMask);
+			m_smokeHits = Physics.OverlapSphereNonAlloc(transform.position + Vector3.up * m_smokeOxygenCheckHeight, m_smokeOxygenCheckRadius, s_hits, s_smokeRayMask);
 			m_smokeHits -= m_oxygenSmokeTolerance;
 			if (m_smokeHits > 0)
 			{
@@ -202,7 +202,7 @@
 		}
 		else
 		{
-			m_inSmoke = Physics.CheckSphere(base.transform.position + Vector3.up * m_smokeCheckHeight, m_smokeCheckRadius, s_smokeRayMask);
+			m_inSmoke = Physics.CheckSphere(transform.position + Vector3.up * m_smokeCheckHeight, m_smokeCheckRadius, s_smokeRayMask);
 			if (m_inSmoke)
 			{
 				m_suffocating++;
@@ -216,7 +216,7 @@
 		if (m_suffocating >= m_maxSmoke && (m_smokeDieChance >= 1f || Random.Range(0f, 1f) < m_smokeDieChance))
 		{
 			Terminal.Log("Fire suffocated");
-			ZNetScene.instance.Destroy(base.gameObject);
+			ZNetScene.instance.Destroy(gameObject);
 		}
 	}
 }
```
