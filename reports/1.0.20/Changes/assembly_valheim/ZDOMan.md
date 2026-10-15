# `ZDOMan.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZDOMan.cs
+++ b/ZDOMan.cs
@@ -284,7 +284,7 @@
 	private bool SaveChunk(List<ZDO> zdos, string fullPath, FileHelpers.FileSource fileSource)
 	{
 		SaveFileHelper.SaveWrite saveWrite = SaveFileHelper.CreateZPackageForWriting(fullPath, fileSource);
-		saveWrite.Pkg.Write((short)41);
+		saveWrite.Pkg.Write((short)42);
 		saveWrite.Pkg.Write(zdos.Count);
 		foreach (ZDO zdo in zdos)
 		{
@@ -2175,7 +2175,7 @@
 			itemData.m_pickedUp = item.GetBool(GetConvertHash(index, "pickedUp", ZDOVars.s_pickedUp), itemData.m_pickedUp);
 			if (worldVersion == Version.World.DeepNorthNoChunk || worldVersion == Version.World.DeepNorthNoChunk2)
 			{
-				itemData.m_cheated = item.GetBool(ZDOVars.s_cheated, itemData.m_cheated);
+				itemData.m_cheated = item.IsCheated(itemData.m_cheated);
 			}
 			ItemDrop.SaveToZDO(itemData, item, index);
 			item.RemoveFloat(ZDOVars.s_durability);
@@ -2198,7 +2198,7 @@
 			}
 			item.RemoveInt(ZDOVars.s_worldLevel);
 			item.RemoveBool(ZDOVars.s_pickedUp);
-			item.RemoveBool(ZDOVars.s_cheated);
+			item.RemoveCheated();
 		}
 		return num;
 	}
```
