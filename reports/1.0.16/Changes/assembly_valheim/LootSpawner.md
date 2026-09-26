# `LootSpawner.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LootSpawner.cs
+++ b/LootSpawner.cs
@@ -41,31 +41,31 @@
 		}
 		if (m_spawnWhenEnemiesCleared)
 		{
-			bool num = IsMonsterInRange(base.transform.position, m_enemiesCheckRange);
-			if (num && !m_seenEnemies)
+			bool flag = IsMonsterInRange(transform.position, m_enemiesCheckRange);
+			if (flag && !m_seenEnemies)
 			{
 				m_seenEnemies = true;
 			}
-			if (num || !m_seenEnemies)
+			if (flag || !m_seenEnemies)
 			{
 				return;
 			}
 		}
-		long num2 = m_nview.GetZDO().GetLong(ZDOVars.s_spawnTime, 0L);
+		long num = m_nview.GetZDO().GetLong(ZDOVars.s_spawnTime, 0L);
 		DateTime time = ZNet.instance.GetTime();
-		DateTime dateTime = new DateTime(num2);
+		DateTime dateTime = new DateTime(num);
 		TimeSpan timeSpan = time - dateTime;
-		if ((!(m_respawnTimeMinuts <= 0f) || num2 == 0L) && !(timeSpan.TotalMinutes < (double)m_respawnTimeMinuts) && Player.IsPlayerInRange(base.transform.position, 20f))
+		if ((!(m_respawnTimeMinuts <= 0f) || num == 0L) && !(timeSpan.TotalMinutes < (double)m_respawnTimeMinuts) && Player.IsPlayerInRange(transform.position, 20f))
 		{
 			List<GameObject> dropList = m_items.GetDropList();
 			for (int i = 0; i < dropList.Count; i++)
 			{
 				Vector2 vector = UnityEngine.Random.insideUnitCircle * 0.3f;
-				Vector3 position = base.transform.position + new Vector3(vector.x, 0.3f * (float)i, vector.y);
+				Vector3 position = transform.position + new Vector3(vector.x, 0.3f * (float)i, vector.y);
 				Quaternion rotation = Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f);
 				UnityEngine.Object.Instantiate(dropList[i], position, rotation);
 			}
-			m_spawnEffect.Create(base.transform.position, Quaternion.identity);
+			m_spawnEffect.Create(transform.position, Quaternion.identity);
 			m_nview.GetZDO().Set(ZDOVars.s_spawnTime, ZNet.instance.GetTime().Ticks);
 			m_seenEnemies = false;
 		}
```
