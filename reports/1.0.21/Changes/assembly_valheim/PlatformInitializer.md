# `PlatformInitializer.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+20/-0` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `InitializeAndLoadPrefs() [Method Body Modified]`
- `InitializeSaveDataStorage() [Method Body Modified]`
- `RetroactivePathFix() [Method Body Modified]`
- `private static void RetroactivePathFix(string[] allFilePaths)`

---

## 📝 Code Diff

```diff
--- a/PlatformInitializer.cs
+++ b/PlatformInitializer.cs
@@ -226,6 +226,26 @@
 		});
 	}
 
+	private static void RetroactivePathFix(string[] allFilePaths)
+	{
+		FileHelpers.Mount(SaveDataAccess.ReadWrite);
+		for (int i = 0; i < allFilePaths.Length; i++)
+		{
+			if (!FileHelpers.ValidPath(allFilePaths[i]))
+			{
+				if (FileHelpers.Delete(allFilePaths[i], FileHelpers.FileSource.Cloud))
+				{
+					ZLog.LogWarning("Deleted file: " + allFilePaths[i] + " since it did not have a valid path.");
+				}
+				else
+				{
+					ZLog.LogError("Needed to delete file " + allFilePaths[i] + " but it failed!");
+				}
+			}
+		}
+		FileHelpers.Unmount();
+	}
+
 	private static void InitializeAndLoadPrefs()
 	{
 		ZLog.Log("Initializing preferences provider...");
```
