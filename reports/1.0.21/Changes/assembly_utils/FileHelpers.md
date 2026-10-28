# `FileHelpers.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+18/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CloudFileWriteInChunks() [Method Body Modified]`
- `GetFileSizes() [Method Body Modified]`
- `GetSourceString() [Method Body Modified]`
- `ValidPath() [Method Body Modified]`
- `public static bool ValidPath(string name)`

---

## 📝 Code Diff

```diff
--- a/FileHelpers.cs
+++ b/FileHelpers.cs
@@ -448,6 +448,15 @@
 		return false;
 	}
 
+	public static bool ValidPath(string name)
+	{
+		if (name != null)
+		{
+			return name.IndexOfAny(Path.GetInvalidPathChars()) == -1;
+		}
+		return false;
+	}
+
 	public static string GetSourceString(FileSource source)
 	{
 		if (source.IsLocal())
@@ -531,13 +540,13 @@
 			if (!Mount(SaveDataAccess.Read))
 			{
 				ZLog.LogError("Mount failed.");
-				return null;
+				return Array.Empty<string>();
 			}
 			if (!CloudStorage.GetAllFilePaths(out var allFilePaths))
 			{
 				ZLog.LogError("Failed to get file paths from connected storage!");
 				Unmount();
-				return null;
+				return Array.Empty<string>();
 			}
 			Unmount();
 			List<string> list = new List<string>();
@@ -829,9 +838,13 @@
 				continue;
 			}
 			string[] files = GetFiles(fileSource, text);
-			foreach (string path in files)
-			{
-				num += GetFileSize(path, fileSource);
+			if (files != null)
+			{
+				string[] array = files;
+				foreach (string path in array)
+				{
+					num += GetFileSize(path, fileSource);
+				}
 			}
 		}
 		return num;
```
