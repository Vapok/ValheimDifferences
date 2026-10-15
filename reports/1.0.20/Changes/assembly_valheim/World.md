# `World.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `LoadWorld() [Method Body Modified]`
- `SaveWorldFWLData() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/World.cs
+++ b/World.cs
@@ -219,7 +219,7 @@
 	{
 		SaveSystem.CheckMove(m_name, SaveDataType.World, ref m_fileSource, now, 0uL);
 		ZPackage zPackage = new ZPackage();
-		zPackage.Write(41);
+		zPackage.Write(42);
 		zPackage.Write(m_name);
 		zPackage.Write(m_seedName);
 		zPackage.Write(m_seed);
@@ -335,7 +335,7 @@
 				return new World(saveFile, SaveDataError.BadVersion);
 			}
 			world2.m_saveNumber = saveNumber;
-			if (world != Version.World.DeepNorth)
+			if (world != Version.World.CheatCleanSlate)
 			{
 				world2.m_createBackupBeforeSaving = true;
 			}
```
