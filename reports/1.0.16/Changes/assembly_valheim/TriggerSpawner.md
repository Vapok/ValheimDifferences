# `TriggerSpawner.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TriggerSpawner.cs
+++ b/TriggerSpawner.cs
@@ -70,7 +70,7 @@
 
 	private void RPC_Trigger(long sender)
 	{
-		ZLog.Log("Trigging " + base.gameObject.name);
+		ZLog.Log("Trigging " + gameObject.name);
 		TrySpawning();
 	}
 
@@ -104,18 +104,18 @@
 
 	private bool Spawn()
 	{
-		Vector3 position = base.transform.position;
+		Vector3 position = transform.position;
 		if (ZoneSystem.instance.FindFloor(position, out var height))
 		{
 			position.y = height;
 		}
 		GameObject gameObject = m_creaturePrefabs[UnityEngine.Random.Range(0, m_creaturePrefabs.Length)];
-		int num = m_maxSpawned + (int)(m_maxExtraPerPlayer * (float)Game.instance.GetPlayerDifficulty(base.transform.position));
-		if (num > 0 && SpawnSystem.GetNrOfInstances(gameObject, base.transform.position, m_maxSpawnedRange) >= num)
+		int num = m_maxSpawned + (int)(m_maxExtraPerPlayer * (float)Game.instance.GetPlayerDifficulty(transform.position));
+		if (num > 0 && SpawnSystem.GetNrOfInstances(gameObject, transform.position, m_maxSpawnedRange) >= num)
 		{
 			return false;
 		}
-		Quaternion rotation = (m_useSpawnerRotation ? base.transform.rotation : Quaternion.Euler(0f, UnityEngine.Random.Range(0f, 360f), 0f));
+		Quaternion rotation = (m_useSpawnerRotation ? transform.rotation : Quaternion.Euler(0f, UnityEngine.Random.Range(0f, 360f), 0f));
 		GameObject gameObject2 = UnityEngine.Object.Instantiate(gameObject, position, rotation);
 		gameObject2.GetComponent<ZNetView>();
 		BaseAI component = gameObject2.GetComponent<BaseAI>();
@@ -150,7 +150,7 @@
 			}
 		}
 		m_nview.GetZDO().Set(ZDOVars.s_spawnTime, ZNet.instance.GetTime().Ticks);
-		m_spawnEffects.Create(base.transform.position, base.transform.rotation);
+		m_spawnEffects.Create(transform.position, transform.rotation);
 		return true;
 	}
 
```
