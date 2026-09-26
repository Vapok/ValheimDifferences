# `ZoneSystem.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+24/-16` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZoneSystem.cs
+++ b/ZoneSystem.cs
@@ -301,7 +301,7 @@
 				return;
 			}
 			m_prefab.Release();
-			m_prefab.m_assetID = default(AssetID);
+			m_prefab.m_assetID = default;
 			if (m_possibleRooms != null)
 			{
 				for (int i = 0; i < m_possibleRooms.Length; i++)
@@ -987,7 +987,7 @@
 			zPackage.Write(item);
 		}
 		zPackage.Write(m_locationVersion);
-		m_tempGlobalKeysSaveClone.RemoveWhere(delegate(string x)
+		m_tempGlobalKeysSaveClone.RemoveWhere((string x) =>
 		{
 			GetKeyValue(x, out var _, out var gk);
 			return gk < GlobalKeys.NonServerOption;
@@ -1559,9 +1559,9 @@
 					}
 					else
 					{
-						GameObject obj2 = UnityEngine.Object.Instantiate(veg.m_prefab, p, identity);
-						obj2.transform.localScale = new Vector3(num10, num10, num10);
-						obj2.transform.SetParent(parent, worldPositionStays: true);
+						GameObject gameObject2 = UnityEngine.Object.Instantiate(veg.m_prefab, p, identity);
+						gameObject2.transform.localScale = new Vector3(num10, num10, num10);
+						gameObject2.transform.SetParent(parent, worldPositionStays: true);
 					}
 					flag2 = true;
 				}
@@ -1810,7 +1810,7 @@
 				{
 					ZLog.DevLog("Loading: Genloc total errors AltBiomeBlock: " + m_totalErrorAltBiomeBlock.ToString("N0", m_split3));
 				}
-				IOrderedEnumerable<KeyValuePair<string, int>> orderedEnumerable = m_placedLocationTries.OrderByDescending(delegate(KeyValuePair<string, int> entry)
+				IOrderedEnumerable<KeyValuePair<string, int>> orderedEnumerable = m_placedLocationTries.OrderByDescending((KeyValuePair<string, int> entry) =>
 				{
 					KeyValuePair<string, int> keyValuePair = entry;
 					return keyValuePair.Value;
@@ -1821,7 +1821,7 @@
 					text += string.Format("\n  {0} \t{1} \ttime: \t{2}", item.Value.ToString("N0", m_split3), item.Key, m_placedLocationTime[item.Key]);
 				}
 				ZLog.DevLog(text);
-				IOrderedEnumerable<KeyValuePair<string, TimeSpan>> orderedEnumerable2 = m_placedLocationTime.OrderByDescending(delegate(KeyValuePair<string, TimeSpan> entry)
+				IOrderedEnumerable<KeyValuePair<string, TimeSpan>> orderedEnumerable2 = m_placedLocationTime.OrderByDescending((KeyValuePair<string, TimeSpan> entry) =>
 				{
 					KeyValuePair<string, TimeSpan> keyValuePair = entry;
 					return keyValuePair.Value;
@@ -1910,7 +1910,15 @@
 					state = UnityEngine.Random.state;
 					UnityEngine.Random.state = insideState;
 				}
-				Vector2s zoneID = (location.m_centerFirst ? GetRandomZone(maxRange) : ((!(location.m_minAltitude < 0f)) ? GetZone(AltBiomeWorldData.MapSpaceToWorldSpace(ZNet.World.m_biomeData.GetRandomPointByBiomesAboveSeaLevel(location.m_biome))) : GetZone(AltBiomeWorldData.MapSpaceToWorldSpace(ZNet.World.m_biomeData.GetRandomPointByBiomes(location.m_biome)))));
+				Vector2s zoneID;
+				if (location.m_centerFirst)
+				{
+					zoneID = GetRandomZone(maxRange);
+				}
+				else
+				{
+					zoneID = ((!(location.m_minAltitude < 0f)) ? GetZone(AltBiomeWorldData.MapSpaceToWorldSpace(ZNet.World.m_biomeData.GetRandomPointByBiomesAboveSeaLevel(location.m_biome))) : GetZone(AltBiomeWorldData.MapSpaceToWorldSpace(ZNet.World.m_biomeData.GetRandomPointByBiomes(location.m_biome))));
+				}
 				if (location.m_centerFirst)
 				{
 					maxRange++;
@@ -2285,7 +2293,7 @@
 		Vector3 zonePos = GetZonePos(GetZone(pos));
 		pos.x = Mathf.Clamp(pos.x, zonePos.x - 32f + num, zonePos.x + 32f - num);
 		pos.z = Mathf.Clamp(pos.z, zonePos.z - 32f + num, zonePos.z + 32f - num);
-		string[] obj = new string[6]
+		string[] array = new string[6]
 		{
 			"radius ",
 			num.ToString(),
@@ -2295,11 +2303,11 @@
 			null
 		};
 		Vector3 vector = zonePos;
-		obj[3] = vector.ToString();
-		obj[4] = " ";
+		array[3] = vector.ToString();
+		array[4] = " ";
 		vector = pos;
-		obj[5] = vector.ToString();
-		ZLog.Log(string.Concat(obj));
+		array[5] = vector.ToString();
+		ZLog.Log(string.Concat(array));
 		MessageHud.instance.ShowMessage(MessageHud.MessageType.Center, "Location spawned, " + (disableSave ? "world saving DISABLED until restart" : "CAUTION! world saving is ENABLED, use normal location command to disable it!"));
 		m_didZoneTest = disableSave;
 		float y = (float)UnityEngine.Random.Range(0, 16) * 22.5f;
@@ -2933,7 +2941,7 @@
 	public bool FindClosestLocation(string name, Vector3 point, out LocationInstance closest)
 	{
 		float num = 999999f;
-		closest = default(LocationInstance);
+		closest = default;
 		bool result = false;
 		foreach (LocationInstance value in m_locationInstances.Values)
 		{
@@ -2987,7 +2995,7 @@
 	{
 		uint num = (uint)(sectorX + 256);
 		uint num2 = (uint)(sectorY + 256);
-		SectorIndex result = default(SectorIndex);
+		SectorIndex result = default;
 		if (num >= 512 || num2 >= 512)
 		{
 			result.Sector = 0u;
@@ -3001,7 +3009,7 @@
 
 	public static SectorIndex IndicesToIndex(uint x, uint y)
 	{
-		SectorIndex result = default(SectorIndex);
+		SectorIndex result = default;
 		if (x >= 512 || y >= 512)
 		{
 			result.Sector = 0u;
```
