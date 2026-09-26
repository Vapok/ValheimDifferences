# `ChunkSaveMapping.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ChunkSaveMapping.cs
+++ b/ChunkSaveMapping.cs
@@ -125,7 +125,7 @@
 		{
 			return null;
 		}
-		string[] obj = new string[8]
+		string[] array = new string[8]
 		{
 			(chunkInfo.m_chunkIndex.Chunk >> 8).ToString("x2"),
 			"_",
@@ -137,11 +137,11 @@
 			null
 		};
 		byte chunkSize = chunkInfo.m_chunkIndex.m_chunkSize;
-		obj[4] = chunkSize.ToString();
-		obj[5] = "_";
-		obj[6] = chunkInfo.m_version.ToString();
-		obj[7] = ".chunk";
-		return string.Concat(obj);
+		array[4] = chunkSize.ToString();
+		array[5] = "_";
+		array[6] = chunkInfo.m_version.ToString();
+		array[7] = ".chunk";
+		return string.Concat(array);
 	}
 
 	public void Load(string saveDirectory, FileHelpers.FileSource fileSource)
```
