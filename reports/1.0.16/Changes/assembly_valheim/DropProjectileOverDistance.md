# `DropProjectileOverDistance.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DropProjectileOverDistance.cs
+++ b/DropProjectileOverDistance.cs
@@ -35,7 +35,7 @@
 		m_nview = GetComponent<ZNetView>();
 		if ((object)m_projectilePrefab == null)
 		{
-			base.enabled = false;
+			enabled = false;
 		}
 	}
 
@@ -45,7 +45,7 @@
 		{
 			return;
 		}
-		Vector3 vector = base.transform.position.Horizontal();
+		Vector3 vector = transform.position.Horizontal();
 		m_distanceAccumulator += Vector3.Distance(lastPosition, vector);
 		Vector3 vector2 = lastPosition.DirTo(vector);
 		if (lastPosition != vector)
@@ -57,7 +57,7 @@
 			m_spawnTimer += Time.deltaTime;
 			if (m_spawnTimer > m_timeToForceSpawn)
 			{
-				SpawnProjectile(base.transform.position, vector2);
+				SpawnProjectile(transform.position, vector2);
 				m_distanceAccumulator -= m_distancePerProjectile;
 				m_distanceAccumulator = Mathf.Max(m_distanceAccumulator, 0f);
 			}
@@ -67,7 +67,7 @@
 			int num = Mathf.FloorToInt(m_distanceAccumulator / m_distancePerProjectile);
 			for (int i = 0; i < Mathf.Min(3, num); i++)
 			{
-				SpawnProjectile(base.transform.position - vector2 * i, vector2);
+				SpawnProjectile(transform.position - vector2 * i, vector2);
 				m_distanceAccumulator -= m_distancePerProjectile;
 				num--;
 			}
@@ -94,9 +94,9 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = new Color(0.76f, 0.52f, 0.55f);
-		Gizmos.DrawLine(base.transform.position, base.transform.position + Vector3.up * m_spawnHeight);
-		Vector3 vector = base.transform.position + base.transform.forward * m_distancePerProjectile;
-		Gizmos.DrawLine(base.transform.position + Vector3.up * 0.5f * m_spawnHeight, vector + Vector3.up * 0.5f * m_spawnHeight);
+		Gizmos.DrawLine(transform.position, transform.position + Vector3.up * m_spawnHeight);
+		Vector3 vector = transform.position + transform.forward * m_distancePerProjectile;
+		Gizmos.DrawLine(transform.position + Vector3.up * 0.5f * m_spawnHeight, vector + Vector3.up * 0.5f * m_spawnHeight);
 		Gizmos.DrawLine(vector, vector + Vector3.up * m_spawnHeight);
 	}
 }
```
