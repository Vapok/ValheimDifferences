# `Odin.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Odin.cs
+++ b/Odin.cs
@@ -25,21 +25,21 @@
 		{
 			return;
 		}
-		Player closestPlayer = Player.GetClosestPlayer(base.transform.position, m_despawnFarDistance);
+		Player closestPlayer = Player.GetClosestPlayer(transform.position, m_despawnFarDistance);
 		if (closestPlayer == null)
 		{
-			m_despawn.Create(base.transform.position, base.transform.rotation);
+			m_despawn.Create(transform.position, transform.rotation);
 			m_nview.Destroy();
 			ZLog.Log("No player in range, despawning");
 			return;
 		}
-		Vector3 forward = closestPlayer.transform.position - base.transform.position;
+		Vector3 forward = closestPlayer.transform.position - transform.position;
 		forward.y = 0f;
 		forward.Normalize();
-		base.transform.rotation = Quaternion.LookRotation(forward);
-		if (Vector3.Distance(closestPlayer.transform.position, base.transform.position) < m_despawnCloseDistance)
+		transform.rotation = Quaternion.LookRotation(forward);
+		if (Vector3.Distance(closestPlayer.transform.position, transform.position) < m_despawnCloseDistance)
 		{
-			m_despawn.Create(base.transform.position, base.transform.rotation);
+			m_despawn.Create(transform.position, transform.rotation);
 			m_nview.Destroy();
 			ZLog.Log("Player go too close,despawning");
 			return;
@@ -47,7 +47,7 @@
 		m_time += Time.deltaTime;
 		if (m_time > m_ttl)
 		{
-			m_despawn.Create(base.transform.position, base.transform.rotation);
+			m_despawn.Create(transform.position, transform.rotation);
 			m_nview.Destroy();
 			ZLog.Log("timeout " + m_time + " , despawning");
 		}
```
