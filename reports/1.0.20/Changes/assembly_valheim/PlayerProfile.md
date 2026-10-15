# `PlayerProfile.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `LoadPlayerFromDisk() [Method Body Modified]`
- `SavePlayerToDisk() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/PlayerProfile.cs
+++ b/PlayerProfile.cs
@@ -250,7 +250,7 @@
 				Directory.CreateDirectory(characterFolderPath);
 			}
 			ZPackage zPackage = new ZPackage();
-			zPackage.Write(46);
+			zPackage.Write(47);
 			zPackage.Write(205);
 			zPackage.Write(10);
 			for (int i = 0; i < 10; i++)
@@ -431,7 +431,7 @@
 				ZLog.Log("Player data is not compatible, ignoring");
 				return false;
 			}
-			if (player != Version.Player.DeepNorth)
+			if (player != Version.Player.CheatCleanSlate)
 			{
 				m_createBackupBeforeSaving = true;
 			}
```
