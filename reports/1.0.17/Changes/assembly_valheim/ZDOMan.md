# `ZDOMan.cs` Diff (`1.0.16` $\rightarrow$ `1.0.17`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZDOMan.cs
+++ b/ZDOMan.cs
@@ -1606,7 +1606,7 @@
 			int x = i % size * num;
 			uint y = (uint)(i / size * num);
 			ZoneSystem.ChunkIndex chunkIndex = ZoneSystem.ChunkIndexFromXY((uint)x, y, chunkSize);
-			if (!m_dirtyChunks[0].Contains(chunkIndex))
+			if (!m_dirtyChunks[0].Contains(chunkIndex) && m_chunkSaveMapping.Chunks.ContainsKey(chunkIndex))
 			{
 				continue;
 			}
```
