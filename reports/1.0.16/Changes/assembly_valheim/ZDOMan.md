# `ZDOMan.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+31/-31` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZDOMan.cs
+++ b/ZDOMan.cs
@@ -431,15 +431,15 @@
 		{
 			return;
 		}
-		string[] obj = new string[7] { "Found ", null, null, null, null, null, null };
+		string[] array = new string[7] { "Found ", null, null, null, null, null, null };
 		value = brokenZDOs.Count;
-		obj[1] = value.ToString();
-		obj[2] = " ZDOs with prefabs not supported. Removing. ";
-		obj[3] = totalNumZDOs.ToString();
-		obj[4] = " => ";
-		obj[5] = numZDOs.ToString();
-		obj[6] = " ZDOs loaded.";
-		ZLog.LogError(string.Concat(obj));
+		array[1] = value.ToString();
+		array[2] = " ZDOs with prefabs not supported. Removing. ";
+		array[3] = totalNumZDOs.ToString();
+		array[4] = " => ";
+		array[5] = numZDOs.ToString();
+		array[6] = " ZDOs loaded.";
+		ZLog.LogError(string.Concat(array));
 		dictionary.Clear();
 		foreach (ZDO brokenZDO in brokenZDOs)
 		{
@@ -469,7 +469,7 @@
 		m_chunkSaveMapping.Load(saveDirectory, fileSource);
 		int numZDOs = m_chunkSaveMapping.GetNumZDOs();
 		int numChunks = m_chunkSaveMapping.GetNumChunks();
-		string[] obj = new string[11]
+		string[] array = new string[11]
 		{
 			"ZDOMan.LoadChunks - Starting to load ",
 			numZDOs.ToString("N0"),
@@ -484,14 +484,14 @@
 			null
 		};
 		long sessionID = m_sessionID;
-		obj[5] = sessionID.ToString();
-		obj[6] = ", WorldVersion: ";
+		array[5] = sessionID.ToString();
+		array[6] = ", WorldVersion: ";
 		int num = (int)version;
-		obj[7] = num.ToString();
-		obj[8] = " [";
-		obj[9] = version.ToString();
-		obj[10] = "]";
-		ZLog.Log(string.Concat(obj));
+		array[7] = num.ToString();
+		array[8] = " [";
+		array[9] = version.ToString();
+		array[10] = "]";
+		ZLog.Log(string.Concat(array));
 		List<ZDO> zdos = new List<ZDO>();
 		zdos.Capacity = numZDOs;
 		List<ZDO> brokenZDOs = new List<ZDO>();
@@ -502,15 +502,15 @@
 			string chunkFilename = m_chunkSaveMapping.GetChunkFilename(chunkIndex2);
 			if (string.IsNullOrEmpty(chunkFilename))
 			{
-				string[] obj2 = new string[6] { "Error: LoadChunks failed to load chunk: ", null, null, null, null, null };
+				string[] array2 = new string[6] { "Error: LoadChunks failed to load chunk: ", null, null, null, null, null };
 				ushort chunk = chunkIndex2.Chunk;
-				obj2[1] = chunk.ToString();
-				obj2[2] = ", size: ";
+				array2[1] = chunk.ToString();
+				array2[2] = ", size: ";
 				byte chunkSize = chunkIndex2.m_chunkSize;
-				obj2[3] = chunkSize.ToString();
-				obj2[4] = ", version: ";
-				obj2[5] = chunkInfo2.m_version.ToString();
-				UnityEngine.Debug.LogError(string.Concat(obj2));
+				array2[3] = chunkSize.ToString();
+				array2[4] = ", version: ";
+				array2[5] = chunkInfo2.m_version.ToString();
+				UnityEngine.Debug.LogError(string.Concat(array2));
 				continue;
 			}
 			string path = saveDirectory + chunkFilename;
@@ -587,7 +587,7 @@
 		ResetBeforeLoad();
 		DirtyPortalObjects = true;
 		m_chunkSaveMapping = new ChunkSaveMapping();
-		string[] obj = new string[9]
+		string[] array = new string[9]
 		{
 			"ZDOMan.Load - Starting to load ",
 			num.ToString("N0"),
@@ -600,14 +600,14 @@
 			null
 		};
 		long sessionID = m_sessionID;
-		obj[3] = sessionID.ToString();
-		obj[4] = ", WorldVersion: ";
+		array[3] = sessionID.ToString();
+		array[4] = ", WorldVersion: ";
 		int num2 = (int)version;
-		obj[5] = num2.ToString();
-		obj[6] = " [";
-		obj[7] = version.ToString();
-		obj[8] = "]";
-		ZLog.Log(string.Concat(obj));
+		array[5] = num2.ToString();
+		array[6] = " [";
+		array[7] = version.ToString();
+		array[8] = "]";
+		ZLog.Log(string.Concat(array));
 		List<ZDO> zdos = new List<ZDO>();
 		zdos.Capacity = num;
 		List<ZDO> brokenZDOs = new List<ZDO>();
```
