# `ChunkSaveMapping.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `Save() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ChunkSaveMapping.cs
+++ b/ChunkSaveMapping.cs
@@ -184,7 +184,7 @@
 				num2++;
 			}
 		}
-		pkg.Write((short)41);
+		pkg.Write((short)42);
 		pkg.Write(num);
 		pkg.Write(num2);
 		foreach (KeyValuePair<ZoneSystem.ChunkIndex, ChunkInfo> chunk2 in m_chunks)
```
