# `DungeonGenerator.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+21/-21` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DungeonGenerator.cs
+++ b/DungeonGenerator.cs
@@ -156,9 +156,9 @@
 
 	public void Clear()
 	{
-		while (base.transform.childCount > 0)
-		{
-			UnityEngine.Object.DestroyImmediate(base.transform.GetChild(0).gameObject);
+		while (transform.childCount > 0)
+		{
+			UnityEngine.Object.DestroyImmediate(transform.GetChild(0).gameObject);
 		}
 	}
 
@@ -182,8 +182,8 @@
 		else
 		{
 			int seed = WorldGenerator.instance.GetSeed();
-			Vector3 position = base.transform.position;
-			Vector2i vector2i = ZoneSystem.GetZone(base.transform.position).ToVector2i();
+			Vector3 position = transform.position;
+			Vector2i vector2i = ZoneSystem.GetZone(transform.position).ToVector2i();
 			m_generatedSeed = seed + vector2i.x * 4271 + vector2i.y * -7187 + (int)position.x * -4271 + (int)position.y * 9187 + (int)position.z * -2134;
 		}
 		m_hasGeneratedSeed = true;
@@ -203,12 +203,12 @@
 		}
 		if ((bool)ZoneSystem.instance)
 		{
-			Vector2s zone = ZoneSystem.GetZone(base.transform.position);
+			Vector2s zone = ZoneSystem.GetZone(transform.position);
 			m_zoneCenter = ZoneSystem.GetZonePos(zone);
-			m_zoneCenter.y = base.transform.position.y - m_originalPosition.y;
+			m_zoneCenter.y = transform.position.y - m_originalPosition.y;
 		}
 		Bounds bounds = new Bounds(m_zoneCenter, m_zoneSize);
-		ZLog.Log($"Generating {base.name}, Seed: {seed}, Bounds diff: {bounds.min - base.transform.position} / {bounds.max - base.transform.position}");
+		ZLog.Log($"Generating {name}, Seed: {seed}, Bounds diff: {bounds.min - transform.position} / {bounds.max - transform.position}");
 		ZLog.Log("Available rooms:" + m_availableRooms.Count);
 		ZLog.Log("To place:" + m_maxRooms);
 		m_placedRooms.Clear();
@@ -259,7 +259,7 @@
 
 	private void OnRoomLoaded(AssetID assetID, LoadResult result)
 	{
-		if (result == LoadResult.Succeeded && !(this == null) && !(base.gameObject == null))
+		if (result == LoadResult.Succeeded && !(this == null) && !(gameObject == null))
 		{
 			m_roomsToLoad--;
 			if (m_roomsToLoad <= 0)
@@ -308,7 +308,7 @@
 	private void GenerateCampGrid(ZoneSystem.SpawnMode mode)
 	{
 		float num = Mathf.Cos(MathF.PI / 180f * m_maxTilt);
-		Vector3 vector = base.transform.position + new Vector3((float)(-m_gridSize) * m_tileWidth * 0.5f, 0f, (float)(-m_gridSize) * m_tileWidth * 0.5f);
+		Vector3 vector = transform.position + new Vector3((float)(-m_gridSize) * m_tileWidth * 0.5f, 0f, (float)(-m_gridSize) * m_tileWidth * 0.5f);
 		for (int i = 0; i < m_gridSize; i++)
 		{
 			for (int j = 0; j < m_gridSize; j++)
@@ -346,7 +346,7 @@
 		int num5 = 0;
 		for (int i = 0; i < num4; i++)
 		{
-			Vector3 p = base.transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * UnityEngine.Random.Range(0f, num - m_perimeterBuffer);
+			Vector3 p = transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * UnityEngine.Random.Range(0f, num - m_perimeterBuffer);
 			DungeonDB.RoomData randomWeightedRoom = GetRandomWeightedRoom(perimeterRoom: false);
 			if (randomWeightedRoom == null)
 			{
@@ -381,7 +381,7 @@
 	{
 		if (room.RoomInPrefab.m_faceCenter)
 		{
-			Vector3 vector = base.transform.position - pos;
+			Vector3 vector = transform.position - pos;
 			vector.y = 0f;
 			if (vector == Vector3.zero)
 			{
@@ -406,7 +406,7 @@
 			{
 				continue;
 			}
-			Vector3 p = base.transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * radius;
+			Vector3 p = transform.position + Quaternion.Euler(0f, UnityEngine.Random.Range(0, 360), 0f) * Vector3.forward * radius;
 			Quaternion campRoomRotation = GetCampRoomRotation(randomWeightedRoom, p);
 			if ((bool)ZoneSystem.instance)
 			{
@@ -527,7 +527,7 @@
 		m_availableRooms.Clear();
 		foreach (DungeonDB.RoomData room in DungeonDB.GetRooms())
 		{
-			if ((room.m_theme & m_themes) != Room.Theme.None && room.m_enabled)
+			if ((room.m_theme & m_themes) != 0 && room.m_enabled)
 			{
 				m_availableRooms.Add(room);
 			}
@@ -728,8 +728,8 @@
 	{
 		DungeonDB.RoomData roomData = FindStartRoom();
 		RoomConnection entrance = roomData.RoomInPrefab.GetEntrance();
-		Quaternion rotation = base.transform.rotation;
-		CalculateRoomPosRot(entrance, base.transform.position, rotation, out var pos, out var rot);
+		Quaternion rotation = transform.rotation;
+		CalculateRoomPosRot(entrance, transform.position, rotation, out var pos, out var rot);
 		PlaceRoom(roomData, pos, rot, entrance, mode);
 	}
 
@@ -808,7 +808,7 @@
 		Vector3 vector = pos;
 		if (m_useCustomInteriorTransform)
 		{
-			vector = pos - base.transform.position;
+			vector = pos - transform.position;
 		}
 		int num = (int)vector.x * 4271 + (int)vector.y * 9187 + (int)vector.z * 2134;
 		if (m_addBaseSeedToRandomSpawn)
@@ -884,7 +884,7 @@
 		{
 			array3[j].gameObject.SetActive(value: false);
 		}
-		Room component2 = SoftReferenceableAssets.Utils.Instantiate(roomData.m_prefab, pos, rot, base.transform).GetComponent<Room>();
+		Room component2 = SoftReferenceableAssets.Utils.Instantiate(roomData.m_prefab, pos, rot, transform).GetComponent<Room>();
 		component2.gameObject.name = roomData.m_prefab.Name;
 		if (mode != ZoneSystem.SpawnMode.Client)
 		{
@@ -943,13 +943,13 @@
 	{
 		if (!(m_colliderA != null))
 		{
-			BoxCollider[] componentsInChildren = base.gameObject.GetComponentsInChildren<BoxCollider>();
+			BoxCollider[] componentsInChildren = gameObject.GetComponentsInChildren<BoxCollider>();
 			for (int i = 0; i < componentsInChildren.Length; i++)
 			{
 				UnityEngine.Object.DestroyImmediate(componentsInChildren[i]);
 			}
-			m_colliderA = base.gameObject.AddComponent<BoxCollider>();
-			m_colliderB = base.gameObject.AddComponent<BoxCollider>();
+			m_colliderA = gameObject.AddComponent<BoxCollider>();
+			m_colliderB = gameObject.AddComponent<BoxCollider>();
 		}
 	}
 
```
