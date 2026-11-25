# `DungeonDB.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `GenerateHashList() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/DungeonDB.cs
+++ b/DungeonDB.cs
@@ -37,7 +37,7 @@
 			}
 		}
 
-		public int Hash => m_prefab.Name.GetStableHashCode();
+		public int Hash => m_prefab.name.GetStableHashCode();
 	}
 
 	private static DungeonDB m_instance;
@@ -107,7 +107,7 @@
 			int hash = room.Hash;
 			if (m_roomByHash.ContainsKey(hash))
 			{
-				ZLog.LogError("Room with name " + room.m_prefab.Name + " already registered");
+				ZLog.LogError("Room with name " + room.m_prefab.name + " already registered");
 			}
 			else
 			{
```
