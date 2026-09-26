# `SmokeSpawner.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SmokeSpawner.cs
+++ b/SmokeSpawner.cs
@@ -38,7 +38,7 @@
 		}
 		foreach (Fire s_fire in Fire.s_fires)
 		{
-			if ((bool)s_fire && Vector3.Distance(s_fire.transform.position, base.transform.position) < m_spawnRadius)
+			if ((bool)s_fire && Vector3.Distance(s_fire.transform.position, transform.position) < m_spawnRadius)
 			{
 				ZNetScene.instance.Destroy(s_fire.gameObject);
 			}
@@ -68,7 +68,7 @@
 	private void Spawn(float time)
 	{
 		Player localPlayer = Player.m_localPlayer;
-		if (localPlayer == null || Vector3.Distance(localPlayer.transform.position, base.transform.position) > 64f)
+		if (localPlayer == null || Vector3.Distance(localPlayer.transform.position, transform.position) > 64f)
 		{
 			m_lastSpawnTime = time;
 		}
@@ -78,7 +78,7 @@
 			{
 				Smoke.FadeOldest();
 			}
-			Vector3 position = base.transform.position;
+			Vector3 position = transform.position;
 			if (m_spawnRadius > 0f)
 			{
 				Vector2 vector = Random.insideUnitCircle.normalized * Random.Range(m_spawnRadius / 2f, m_spawnRadius);
@@ -91,7 +91,7 @@
 
 	private bool TestBlocked()
 	{
-		if (Physics.CheckSphere(base.transform.position, m_testRadius, m_testMask.value))
+		if (Physics.CheckSphere(transform.position, m_testRadius, m_testMask.value))
 		{
 			return true;
 		}
@@ -100,7 +100,7 @@
 
 	public bool IsBlocked()
 	{
-		if (!base.gameObject.activeInHierarchy)
+		if (!gameObject.activeInHierarchy)
 		{
 			return TestBlocked();
 		}
@@ -110,6 +110,6 @@
 	private void OnDrawGizmos()
 	{
 		Gizmos.color = Color.yellow;
-		Utils.DrawGizmoCircle(base.transform.position, m_spawnRadius, 16);
+		Utils.DrawGizmoCircle(transform.position, m_spawnRadius, 16);
 	}
 }
```
