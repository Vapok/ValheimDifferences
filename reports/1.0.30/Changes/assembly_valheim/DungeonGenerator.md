# `DungeonGenerator.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `PlaceEndCaps() [Method Body Modified]`
- `PlaceRoom() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/DungeonGenerator.cs
+++ b/DungeonGenerator.cs
@@ -621,7 +621,7 @@
 						if (!flag)
 						{
 							PlaceRoom(weightedRoom, pos, rot, roomConnection, mode);
-							ZLog.Log("Cyclic detected. Door missmatch for cyclic room '" + roomConnection.m_type + "'-'" + roomConnection2.m_type + "', placing divider: " + weightedRoom.m_prefab.Name);
+							ZLog.Log("Cyclic detected. Door missmatch for cyclic room '" + roomConnection.m_type + "'-'" + roomConnection2.m_type + "', placing divider: " + weightedRoom.m_prefab.name);
 						}
 					}
 					else
@@ -884,8 +884,8 @@
 		{
 			array3[j].gameObject.SetActive(value: false);
 		}
-		Room component2 = SoftReferenceableAssets.Utils.Instantiate(roomData.m_prefab, pos, rot, transform).GetComponent<Room>();
-		component2.gameObject.name = roomData.m_prefab.Name;
+		Room component2 = roomData.m_prefab.Instantiate(pos, rot, transform).GetComponent<Room>();
+		component2.gameObject.name = roomData.m_prefab.name;
 		if (mode != ZoneSystem.SpawnMode.Client)
 		{
 			component2.m_placeOrder = (fromConnection ? (fromConnection.m_placeOrder + 1) : 0);
```
