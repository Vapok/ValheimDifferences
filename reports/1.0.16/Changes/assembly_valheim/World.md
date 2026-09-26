# `World.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/World.cs
+++ b/World.cs
@@ -316,7 +316,7 @@
 			world2.m_chunkedSave = flag;
 			if (flag != world >= Version.World.ChunkedSave)
 			{
-				string[] obj = new string[9]
+				string[] array = new string[9]
 				{
 					"Save file seems to be chunked save, but Version is too low. World: ",
 					world2.m_worldName,
@@ -329,9 +329,9 @@
 					null
 				};
 				int num = (int)world;
-				obj[7] = num.ToString();
-				obj[8] = "]";
-				ZLog.LogError(string.Concat(obj));
+				array[7] = num.ToString();
+				array[8] = "]";
+				ZLog.LogError(string.Concat(array));
 				return new World(saveFile, SaveDataError.BadVersion);
 			}
 			world2.m_saveNumber = saveNumber;
```
