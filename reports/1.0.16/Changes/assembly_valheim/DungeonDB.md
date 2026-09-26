# `DungeonDB.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DungeonDB.cs
+++ b/DungeonDB.cs
@@ -122,7 +122,7 @@
 		{
 			return;
 		}
-		ReferenceHolder referenceHolder = base.gameObject.AddComponent<ReferenceHolder>();
+		ReferenceHolder referenceHolder = gameObject.AddComponent<ReferenceHolder>();
 		foreach (RoomData room in m_rooms)
 		{
 			if (room.m_enabled)
```
