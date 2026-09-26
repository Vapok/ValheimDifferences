# `SaveSystem.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+33/-19` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SaveSystem.cs
+++ b/SaveSystem.cs
@@ -258,7 +258,7 @@
 	{
 		return dataType switch
 		{
-			SaveDataType.World => new WorldSaveComparer(), 
+			SaveDataType.World => (IComparer<string>)new WorldSaveComparer(), 
 			SaveDataType.Character => new CharacterSaveComparer(), 
 			_ => null, 
 		};
@@ -590,9 +590,14 @@
 		{
 			return RestoreBackupResult.UnknownError;
 		}
-		if (!FileHelpers.Mount(SaveDataAccess.ReadWrite))
-		{
-			return RestoreBackupResult.UnknownError;
+		bool flag = false;
+		if (backup.m_source.IsCloud())
+		{
+			if (!FileHelpers.Mount(SaveDataAccess.ReadWrite))
+			{
+				return RestoreBackupResult.UnknownError;
+			}
+			flag = true;
 		}
 		SaveWithBackups parentSaveWithBackups = backup.ParentSaveWithBackups;
 		if (backup.IsChunked)
@@ -601,22 +606,31 @@
 		}
 		if (!parentSaveWithBackups.IsDeleted && !Rename(parentSaveWithBackups.PrimaryFile, parentSaveWithBackups.Name + "_backup_restore-" + DateTime.Now.ToString(s_defaultDateFormat)))
 		{
+			if (flag)
+			{
+				FileHelpers.Unmount();
+			}
+			return RestoreBackupResult.RenameFailed;
+		}
+		string newName = parentSaveWithBackups.Name + "_backup_" + DateTime.Now.ToString(s_defaultDateFormat);
+		bool flag2 = false;
+		if (saveFileType != SaveFileType.Single)
+		{
+			newName = parentSaveWithBackups.Name;
+			flag2 = backup.m_source.IsLocal() && saveFileType == SaveFileType.CloudBackup;
+		}
+		if (Copy(backup, newName, flag2 ? FileHelpers.FileSource.Cloud : backup.m_source))
+		{
+			if (flag)
+			{
+				FileHelpers.Unmount();
+			}
+			return RestoreBackupResult.Success;
+		}
+		if (flag)
+		{
 			FileHelpers.Unmount();
-			return RestoreBackupResult.RenameFailed;
-		}
-		string newName = parentSaveWithBackups.Name + "_backup_" + DateTime.Now.ToString(s_defaultDateFormat);
-		bool flag = false;
-		if (saveFileType != SaveFileType.Single)
-		{
-			newName = parentSaveWithBackups.Name;
-			flag = backup.m_source.IsLocal() && saveFileType == SaveFileType.CloudBackup;
-		}
-		if (Copy(backup, newName, flag ? FileHelpers.FileSource.Cloud : backup.m_source))
-		{
-			FileHelpers.Unmount();
-			return RestoreBackupResult.Success;
-		}
-		FileHelpers.Unmount();
+		}
 		return RestoreBackupResult.CopyFailed;
 	}
 
```
