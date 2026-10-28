# `SaveCollection.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+66/-21` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `EnsureLocalLoaded() [Method Body Modified]`
- `GetAllFilesInSource() [Method Body Modified]`
- `KeepOnlyNewest() [Method Body Modified]`
- `Reload() [Method Body Modified]`
- `ReloadLocal() [Method Body Modified]`
- `SourceByIndexAndEntryCount() [Method Body Modified]`
- `TryGetSaveByName() [Method Body Modified]`
- `private void GetAllFilesInSource(SaveDataType dataType, FileHelpers.FileSource source, ref List<string> listToAddTo)`
- `private void ReloadLocal()`
- `public void EnsureLocalLoaded()`
- `static void GetAllFilesInSource(SaveDataType dataType, FileHelpers.FileSource source, ref List<string> reference)`

---

## 📝 Code Diff

```diff
--- a/SaveCollection.cs
+++ b/SaveCollection.cs
@@ -62,6 +62,14 @@
 	{
 		EnsureLoaded();
 		return m_savesByName.TryGetValue(name, out save);
+	}
+
+	public void EnsureLocalLoaded()
+	{
+		if (m_needsReload)
+		{
+			ReloadLocal();
+		}
 	}
 
 	private void Reload()
@@ -136,27 +144,64 @@
 		m_needsReload = false;
 		SetNeedsSort();
 		ZLog.Log("SaveSystem.Reload for " + m_dataType.ToString() + " is done [" + stopwatch.ElapsedMilliseconds.ToString("N0") + "ms]");
-		static void GetAllFilesInSource(SaveDataType dataType, FileHelpers.FileSource source, ref List<string> reference)
-		{
-			string savePath = SaveSystem.GetSavePath(dataType, source);
-			string[] files = FileHelpers.GetFiles(source, savePath);
-			if (files != null)
-			{
-				reference.AddRange(files);
-			}
-		}
-		static FileHelpers.FileSource SourceByIndexAndEntryCount(int cloudEntriesIndex, int localEntriesIndex, int index)
-		{
-			if (index < cloudEntriesIndex)
-			{
-				return FileHelpers.FileSource.Cloud;
-			}
-			if (index < localEntriesIndex)
-			{
-				return FileHelpers.FileSource.Local;
-			}
-			return FileHelpers.FileSource.Legacy;
-		}
+	}
+
+	private void ReloadLocal()
+	{
+		Stopwatch stopwatch = Stopwatch.StartNew();
+		List<string> listToAddTo = new List<string>();
+		Dictionary<FileHelpers.FileSource, Dictionary<string, List<string>>> allChunkedSaves = new Dictionary<FileHelpers.FileSource, Dictionary<string, List<string>>>();
+		if (Directory.Exists(SaveSystem.GetSavePath(m_dataType, FileHelpers.FileSource.Local)))
+		{
+			GetAllFilesInSource(m_dataType, FileHelpers.FileSource.Local, ref listToAddTo);
+		}
+		KeepOnlyNewest(ref listToAddTo, ref allChunkedSaves, FileHelpers.FileSource.Local);
+		List<string> list = new List<string>();
+		listToAddTo.Sort(SaveSystem.GetComparerByDataType(m_dataType));
+		list.AddRange(listToAddTo);
+		foreach (SaveWithBackups safe in m_saves)
+		{
+			if (safe.PrimaryFile == null || safe.PrimaryFile.m_source != FileHelpers.FileSource.Cloud)
+			{
+				safe.ClearSaveFiles();
+			}
+		}
+		foreach (var (fileSource2, dictionary2) in allChunkedSaves)
+		{
+			foreach (var (_, list3) in dictionary2)
+			{
+				if (SaveSystem.GetSaveInfo(list3[0], out var saveName, out var _, out var _, out var _) && m_savesByName.TryGetValue(saveName, out var value) && (value.PrimaryFile == null || value.PrimaryFile.m_source != FileHelpers.FileSource.Cloud))
+				{
+					value.AddSaveFile(list3.ToArray(), fileSource2);
+				}
+			}
+		}
+		m_needsReload = false;
+		SetNeedsSort();
+		ZLog.Log("SaveSystem.ReloadLocal for " + m_dataType.ToString() + " is done [" + stopwatch.ElapsedMilliseconds.ToString("N0") + "ms]");
+	}
+
+	private void GetAllFilesInSource(SaveDataType dataType, FileHelpers.FileSource source, ref List<string> listToAddTo)
+	{
+		string savePath = SaveSystem.GetSavePath(dataType, source);
+		string[] files = FileHelpers.GetFiles(source, savePath);
+		if (files != null)
+		{
+			listToAddTo.AddRange(files);
+		}
+	}
+
+	private FileHelpers.FileSource SourceByIndexAndEntryCount(int cloudEntriesIndex, int localEntriesIndex, int index)
+	{
+		if (index < cloudEntriesIndex)
+		{
+			return FileHelpers.FileSource.Cloud;
+		}
+		if (index < localEntriesIndex)
+		{
+			return FileHelpers.FileSource.Local;
+		}
+		return FileHelpers.FileSource.Legacy;
 	}
 
 	private void KeepOnlyNewest(ref List<string> allFiles, ref Dictionary<FileHelpers.FileSource, Dictionary<string, List<string>>> allChunkedSaves, FileHelpers.FileSource fileSource)
```
