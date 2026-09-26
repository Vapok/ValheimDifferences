# `CinderSpawner.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/CinderSpawner.cs
+++ b/CinderSpawner.cs
@@ -49,10 +49,10 @@
 			Projectile component = GetComponent<Projectile>();
 			if ((object)component != null)
 			{
-				component.m_onHit = (OnProjectileHit)Delegate.Combine(component.m_onHit, (OnProjectileHit)delegate
+				component.m_onHit = (OnProjectileHit)Delegate.Combine(component.m_onHit, (OnProjectileHit)((Collider collider, Vector3 point, bool water) =>
 				{
 					SpawnCinder();
-				});
+				}));
 			}
 		}
 		m_fireplace = GetComponent<Fireplace>();
@@ -88,21 +88,21 @@
 
 	public void SpawnCinder()
 	{
-		if (m_nview.IsValid() && m_nview.IsOwner() && CanSpawnCinder() && !ShieldGenerator.IsInsideShield(base.transform.position))
+		if (m_nview.IsValid() && m_nview.IsOwner() && CanSpawnCinder() && !ShieldGenerator.IsInsideShield(transform.position))
 		{
 			for (int i = 0; i < m_instancesPerSpawn; i++)
 			{
 				Vector3 insideUnitSphere = UnityEngine.Random.insideUnitSphere;
 				insideUnitSphere.y = Mathf.Abs(insideUnitSphere.y * 2f);
 				insideUnitSphere.Normalize();
-				UnityEngine.Object.Instantiate(m_cinderPrefab, base.transform.position + insideUnitSphere * m_spawnOffset, Quaternion.identity).GetComponent<Cinder>().Setup(insideUnitSphere * m_cinderVel, GetSpread() - 1);
+				UnityEngine.Object.Instantiate(m_cinderPrefab, transform.position + insideUnitSphere * m_spawnOffset, Quaternion.identity).GetComponent<Cinder>().Setup(insideUnitSphere * m_cinderVel, GetSpread() - 1);
 			}
 		}
 	}
 
 	public bool CanSpawnCinder()
 	{
-		return CanSpawnCinder(base.transform, ref m_biome);
+		return CanSpawnCinder(transform, ref m_biome);
 	}
 
 	public static bool CanSpawnCinder(Transform transform, ref Heightmap.Biome biome)
@@ -134,6 +134,6 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.cyan;
-		Gizmos.DrawWireSphere(base.transform.position + m_spawnOffsetPoint, 0.05f);
+		Gizmos.DrawWireSphere(transform.position + m_spawnOffsetPoint, 0.05f);
 	}
 }
```
