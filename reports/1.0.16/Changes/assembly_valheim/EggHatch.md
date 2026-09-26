# `EggHatch.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/EggHatch.cs
+++ b/EggHatch.cs
@@ -28,7 +28,7 @@
 	{
 		if (m_nview.IsValid() && m_nview.IsOwner())
 		{
-			Player closestPlayer = Player.GetClosestPlayer(base.transform.position, m_triggerDistance);
+			Player closestPlayer = Player.GetClosestPlayer(transform.position, m_triggerDistance);
 			if ((bool)closestPlayer && !closestPlayer.InGhostMode())
 			{
 				Hatch();
@@ -38,8 +38,8 @@
 
 	private void Hatch()
 	{
-		m_hatchEffect.Create(base.transform.position, base.transform.rotation);
-		Object.Instantiate(m_spawnPrefab, base.transform.TransformPoint(m_spawnOffset), Quaternion.Euler(0f, Random.Range(0, 360), 0f));
+		m_hatchEffect.Create(transform.position, transform.rotation);
+		Object.Instantiate(m_spawnPrefab, transform.TransformPoint(m_spawnOffset), Quaternion.Euler(0f, Random.Range(0, 360), 0f));
 		m_nview.Destroy();
 	}
 }
```
