# `SpawnArea.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SpawnArea.cs
+++ b/SpawnArea.cs
@@ -55,7 +55,7 @@
 
 	private void UpdateSpawn()
 	{
-		if (m_nview.IsOwner() && !ZNetScene.instance.OutsideActiveArea(base.transform.position) && Player.IsPlayerInRange(base.transform.position, m_triggerDistance))
+		if (m_nview.IsOwner() && !ZNetScene.instance.OutsideActiveArea(transform.position) && Player.IsPlayerInRange(transform.position, m_triggerDistance))
 		{
 			m_spawnTimer += 2f;
 			if (m_spawnTimer > m_spawnIntervalSec)
@@ -121,7 +121,7 @@
 		prefab.GetComponent<BaseAI>();
 		for (int i = 0; i < 10; i++)
 		{
-			Vector3 vector = base.transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * UnityEngine.Random.Range(0f, m_spawnRadius);
+			Vector3 vector = transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * UnityEngine.Random.Range(0f, m_spawnRadius);
 			if (ZoneSystem.instance.FindFloor(vector, out var height) && (!m_onGroundOnly || !ZoneSystem.instance.IsBlocked(vector)))
 			{
 				vector.y = height + 0.1f;
@@ -161,7 +161,7 @@
 	{
 		near = 0;
 		total = 0;
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		foreach (BaseAI baseAIInstance in BaseAI.BaseAIInstances)
 		{
 			if (IsSpawnPrefab(baseAIInstance.gameObject))
@@ -195,7 +195,7 @@
 
 	public float GetLevelUpChance()
 	{
-		float levelUpChanceMultiplier = WorldGenerator.instance.GetBiomeSector(base.transform.position).GetLevelUpChanceMultiplier();
+		float levelUpChanceMultiplier = WorldGenerator.instance.GetBiomeSector(transform.position).GetLevelUpChanceMultiplier();
 		if (Game.m_worldLevel > 0 && Game.instance.m_worldLevelEnemyLevelUpExponent > 0f)
 		{
 			return Mathf.Min(70f, Mathf.Pow(m_levelupChance, (float)Game.m_worldLevel * Game.instance.m_worldLevelEnemyLevelUpExponent)) * levelUpChanceMultiplier;
@@ -206,8 +206,8 @@
 	private void OnDrawGizmosSelected()
 	{
 		Gizmos.color = Color.red;
-		Gizmos.DrawWireSphere(base.transform.position, m_spawnRadius);
+		Gizmos.DrawWireSphere(transform.position, m_spawnRadius);
 		Gizmos.color = Color.yellow;
-		Gizmos.DrawWireSphere(base.transform.position, m_nearRadius);
+		Gizmos.DrawWireSphere(transform.position, m_nearRadius);
 	}
 }
```
