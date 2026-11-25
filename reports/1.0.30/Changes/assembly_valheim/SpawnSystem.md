# `SpawnSystem.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateSpawnList() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/SpawnSystem.cs
+++ b/SpawnSystem.cs
@@ -192,10 +192,10 @@
 		m_tempNearZDOs.Clear();
 		ZDOMan.instance.FindSectorObjects(ZoneSystem.GetZone(transform.position), SimulationDistance.OriginalDistance, m_tempNearZDOs);
 		int num = 0;
-		int num2 = 0;
 		foreach (SpawnData spawner in spawners)
 		{
-			num2++;
+			int num2 = 0;
+			num++;
 			if (!spawner.m_enabled || !m_heightmap.HaveBiome(spawner.m_biome))
 			{
 				continue;
@@ -213,7 +213,7 @@
 			{
 				continue;
 			}
-			int stableHashCode = (groupSalt + spawner.m_prefab.name + num2).GetStableHashCode();
+			int stableHashCode = (groupSalt + spawner.m_prefab.name + num).GetStableHashCode();
 			DateTime dateTime = new DateTime(m_nview.GetZDO().GetLong(stableHashCode, 0L));
 			TimeSpan timeSpan = currentTime - dateTime;
 			int num3 = Mathf.Min((spawner.m_maxSpawned == 0) ? 1 : spawner.m_maxSpawned, (int)(timeSpan.TotalSeconds / (double)spawner.m_spawnInterval));
@@ -235,7 +235,7 @@
 				if (spawner.m_maxSpawned > 0)
 				{
 					num4 = GetNrOfZDOInstances(spawner.m_prefab, m_tempNearZDOs, eventSpawners);
-					if (num4 + num >= spawner.m_maxSpawned)
+					if (num4 + num2 >= spawner.m_maxSpawned)
 					{
 						break;
 					}
@@ -266,7 +266,7 @@
 					if (IsSpawnPointGood(spawner, ref spawnPoint))
 					{
 						Spawn(spawner, spawnPoint + Vector3.up * (spawner.m_groundOffset + UnityEngine.Random.Range(0f, spawner.m_groundOffsetRandom)), eventSpawners);
-						num++;
+						num2++;
 						num7++;
 						if (num7 >= num5)
 						{
```
