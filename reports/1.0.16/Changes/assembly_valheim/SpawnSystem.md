# `SpawnSystem.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+21/-19` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SpawnSystem.cs
+++ b/SpawnSystem.cs
@@ -146,7 +146,7 @@
 	{
 		m_instances.Add(this);
 		m_nview = GetComponent<ZNetView>();
-		m_heightmap = Heightmap.FindHeightmap(base.transform.position);
+		m_heightmap = Heightmap.FindHeightmap(transform.position);
 		InvokeRepeating("UpdateSpawning", 10f, 1f);
 	}
 
@@ -190,11 +190,12 @@
 	private void UpdateSpawnList(List<SpawnData> spawners, DateTime currentTime, bool eventSpawners, string groupSalt)
 	{
 		m_tempNearZDOs.Clear();
-		ZDOMan.instance.FindSectorObjects(ZoneSystem.GetZone(base.transform.position), SimulationDistance.OriginalDistance, m_tempNearZDOs);
+		ZDOMan.instance.FindSectorObjects(ZoneSystem.GetZone(transform.position), SimulationDistance.OriginalDistance, m_tempNearZDOs);
 		int num = 0;
+		int num2 = 0;
 		foreach (SpawnData spawner in spawners)
 		{
-			num++;
+			num2++;
 			if (!spawner.m_enabled || !m_heightmap.HaveBiome(spawner.m_biome))
 			{
 				continue;
@@ -212,15 +213,15 @@
 			{
 				continue;
 			}
-			int stableHashCode = (groupSalt + spawner.m_prefab.name + num).GetStableHashCode();
+			int stableHashCode = (groupSalt + spawner.m_prefab.name + num2).GetStableHashCode();
 			DateTime dateTime = new DateTime(m_nview.GetZDO().GetLong(stableHashCode, 0L));
 			TimeSpan timeSpan = currentTime - dateTime;
-			int num2 = Mathf.Min((spawner.m_maxSpawned == 0) ? 1 : spawner.m_maxSpawned, (int)(timeSpan.TotalSeconds / (double)spawner.m_spawnInterval));
-			if (num2 > 0)
+			int num3 = Mathf.Min((spawner.m_maxSpawned == 0) ? 1 : spawner.m_maxSpawned, (int)(timeSpan.TotalSeconds / (double)spawner.m_spawnInterval));
+			if (num3 > 0)
 			{
 				m_nview.GetZDO().Set(stableHashCode, currentTime.Ticks);
 			}
-			for (int i = 0; i < num2; i++)
+			for (int i = 0; i < num3; i++)
 			{
 				if (UnityEngine.Random.Range(0f, 100f) > spawner.m_spawnChance)
 				{
@@ -230,11 +231,11 @@
 				{
 					break;
 				}
-				int num3 = 0;
+				int num4 = 0;
 				if (spawner.m_maxSpawned > 0)
 				{
-					num3 = GetNrOfZDOInstances(spawner.m_prefab, m_tempNearZDOs, eventSpawners);
-					if (num3 >= spawner.m_maxSpawned)
+					num4 = GetNrOfZDOInstances(spawner.m_prefab, m_tempNearZDOs, eventSpawners);
+					if (num4 + num >= spawner.m_maxSpawned)
 					{
 						break;
 					}
@@ -255,24 +256,25 @@
 				{
 					continue;
 				}
-				int num4 = Mathf.Min(UnityEngine.Random.Range(spawner.m_groupSizeMin, spawner.m_groupSizeMax + 1), (spawner.m_maxSpawned > 0) ? (spawner.m_maxSpawned - num3) : 100);
-				float num5 = ((num4 > 1) ? spawner.m_groupRadius : 0f);
-				int num6 = 0;
-				for (int j = 0; j < num4 * 2; j++)
+				int num5 = Mathf.Min(UnityEngine.Random.Range(spawner.m_groupSizeMin, spawner.m_groupSizeMax + 1), (spawner.m_maxSpawned > 0) ? (spawner.m_maxSpawned - num4) : 100);
+				float num6 = ((num5 > 1) ? spawner.m_groupRadius : 0f);
+				int num7 = 0;
+				for (int j = 0; j < num5 * 2; j++)
 				{
 					Vector2 insideUnitCircle = UnityEngine.Random.insideUnitCircle;
-					Vector3 spawnPoint = spawnCenter + new Vector3(insideUnitCircle.x, 0f, insideUnitCircle.y) * num5;
+					Vector3 spawnPoint = spawnCenter + new Vector3(insideUnitCircle.x, 0f, insideUnitCircle.y) * num6;
 					if (IsSpawnPointGood(spawner, ref spawnPoint))
 					{
 						Spawn(spawner, spawnPoint + Vector3.up * (spawner.m_groundOffset + UnityEngine.Random.Range(0f, spawner.m_groundOffsetRandom)), eventSpawners);
-						num6++;
-						if (num6 >= num4)
+						num++;
+						num7++;
+						if (num7 >= num5)
 						{
 							break;
 						}
 					}
 				}
-				ZLog.Log("Spawned " + spawner.m_prefab.name + " x " + num6);
+				ZLog.Log("Spawned " + spawner.m_prefab.name + " x " + num7);
 			}
 		}
 	}
@@ -590,7 +592,7 @@
 	private bool InsideZone(Vector3 point, float extra = 0f)
 	{
 		float num = 32f + extra;
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		if (point.x < position.x - num || point.x > position.x + num)
 		{
 			return false;
```
