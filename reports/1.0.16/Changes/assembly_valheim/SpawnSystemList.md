# `SpawnSystemList.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SpawnSystemList.cs
+++ b/SpawnSystemList.cs
@@ -12,7 +12,7 @@
 	{
 		foreach (SpawnSystem.SpawnData spawner in m_spawners)
 		{
-			if ((spawner.m_biome & biome) != Heightmap.Biome.None || spawner.m_biome == biome)
+			if ((spawner.m_biome & biome) != 0 || spawner.m_biome == biome)
 			{
 				spawners.Add(spawner);
 			}
```
