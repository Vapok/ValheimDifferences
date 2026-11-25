# `ZoneSystem.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+22/-22` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CheckLocationDuplicates() [Method Body Modified]`
- `CountNrOfLocation() [Method Body Modified]`
- `CreateLocationProxy() [Method Body Modified]`
- `FindClosestLocation() [Method Body Modified]`
- `FindLocations() [Method Body Modified]`
- `GenerateLocationsTimeSliced() [Method Body Modified]`
- `GetGlobalKey() [Method Body Modified]`
- `GetGlobalKeyExact() [Method Body Modified]`
- `GetLocation() [Method Body Modified]`
- `GetLocationIcon() [Method Body Modified]`
- `GetLocationIcons() [Method Body Modified]`
- `PlaceLocations() [Method Body Modified]`
- `SetupLocations() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ZoneSystem.cs
+++ b/ZoneSystem.cs
@@ -241,7 +241,7 @@
 
 		private string m_altBiomeParent;
 
-		public int Hash => m_prefab.Name.GetStableHashCode();
+		public int Hash => m_prefab.name.GetStableHashCode();
 
 		public string AltBiomeParent
 		{
@@ -554,7 +554,7 @@
 
 	public HashSet<GlobalKeys> m_globalKeysEnums = new HashSet<GlobalKeys>();
 
-	public Dictionary<string, string> m_globalKeysValues = new Dictionary<string, string>();
+	public Dictionary<string, string> m_globalKeysValues = new Dictionary<string, string>(StringComparer.OrdinalIgnoreCase);
 
 	private HashSet<Vector2s> m_tempGeneratedZonesSaveClone;
 
@@ -908,7 +908,7 @@
 		{
 			if ((location.m_enable || location.m_prefab.IsValid) && Application.isPlaying)
 			{
-				location.m_prefabName = location.m_prefab.Name;
+				location.m_prefabName = location.m_prefab.name;
 				int hash = location.Hash;
 				if (!m_locationsByHash.ContainsKey(hash))
 				{
@@ -1606,7 +1606,7 @@
 					throw new NullReferenceException($"Location in list of locations was invalid! Asset: {location.m_prefab.m_assetID}");
 				}
 			}
-			else if (location.m_prefab.Name == name)
+			else if (location.m_prefab.name == name)
 			{
 				return location;
 			}
@@ -1662,7 +1662,7 @@
 				ZoneLocation zoneLocation2 = m_locations[j];
 				if (zoneLocation2.m_enable)
 				{
-					if (zoneLocation.m_prefab.Name == zoneLocation2.m_prefab.Name)
+					if (zoneLocation.m_prefab.name == zoneLocation2.m_prefab.name)
 					{
 						SoftReference<GameObject> prefab = zoneLocation.m_prefab;
 						ZLog.LogWarning("Two locations have the same location prefab name " + prefab.ToString());
@@ -1855,7 +1855,7 @@
 		int num = 0;
 		foreach (LocationInstance value in m_locationInstances.Values)
 		{
-			if (value.m_location.m_prefab.Name == location.m_prefab.Name)
+			if (value.m_location.m_prefab.name == location.m_prefab.name)
 			{
 				num++;
 			}
@@ -1871,7 +1871,7 @@
 	private IEnumerator GenerateLocationsTimeSliced(ZoneLocation location, Stopwatch timeSliceStopwatch, ZPackage iterationsPkg)
 	{
 		DateTime t = DateTime.Now;
-		int seed = WorldGenerator.instance.GetSeed() + location.m_prefab.Name.GetStableHashCode();
+		int seed = WorldGenerator.instance.GetSeed() + location.m_prefab.name.GetStableHashCode();
 		UnityEngine.Random.State state = UnityEngine.Random.state;
 		UnityEngine.Random.InitState(seed);
 		int errorLocationInZone = 0;
@@ -2086,7 +2086,7 @@
 			TimeSpan timeSpan = DateTime.Now - t;
 			if (UnityEngine.Debug.isDebugBuild)
 			{
-				string key = $"{location.m_prefab.Name} ({((placed < location.m_quantity) ? $"{placed} / {location.m_quantity}" : ((object)location.m_quantity))})";
+				string key = $"{location.m_prefab.name} ({((placed < location.m_quantity) ? $"{placed} / {location.m_quantity}" : ((object)location.m_quantity))})";
 				m_placedLocationTries[key] = num12;
 				m_placedLocationTime[key] = timeSpan;
 			}
@@ -2094,15 +2094,15 @@
 			{
 				m_slowLocations++;
 				m_slowLocationTime += (float)timeSpan.TotalSeconds;
-				ZLog.LogWarning($"Location {location.m_prefab.Name} took more than {0.5f} seconds to place, check spawn conditions to improve! (placed {placed} out of {location.m_quantity} with {num12})");
+				ZLog.LogWarning($"Location {location.m_prefab.name} took more than {0.5f} seconds to place, check spawn conditions to improve! (placed {placed} out of {location.m_quantity} with {num12})");
 			}
 			if (placed < location.m_quantity)
 			{
-				ZLog.LogWarning($"Failed to place all {location.m_prefab.Name}, placed {placed} out of {location.m_quantity} with {num12} tries in {timeSpan}");
+				ZLog.LogWarning($"Failed to place all {location.m_prefab.name}, placed {placed} out of {location.m_quantity} with {num12} tries in {timeSpan}");
 				if (UnityEngine.Debug.isDebugBuild)
 				{
 					m_totalUnplaceableErrors += num12;
-					m_unplaceableLocations.Add($"{location.m_prefab.Name} (placed: {placed}/{location.m_quantity}, errors: {num12})");
+					m_unplaceableLocations.Add($"{location.m_prefab.name} (placed: {placed}/{location.m_quantity}, errors: {num12})");
 					ZLog.DevLog("      errorLocationInZone " + errorLocationInZone);
 					ZLog.DevLog("      errorBiomeArea " + errorBiomeArea);
 					ZLog.DevLog("      errorCenterDistance " + errorCenterDistance);
@@ -2119,7 +2119,7 @@
 			}
 			else if (UnityEngine.Debug.isDebugBuild)
 			{
-				ZLog.DevLog($"Placed all {location.m_quantity} {location.m_prefab.Name} with {num12} tries in {timeSpan} ..." + "\n      errorLocationInZone " + errorLocationInZone + "\n      errorBiomeArea " + errorBiomeArea + "\n      errorCenterDistance " + errorCenterDistance + "\n      errorBiome " + errorBiome + "\n      errorAltitude " + errorAltitude + "\n      errorForest " + errorForest + "\n      errorTerrainDelta " + errorTerrainDelta + "\n      errorSimilar " + errorSimilar + "\n      errorNotSimilar " + errorNotSimilar + "\n      errorVegetation " + errorVegetation + "\n      errorAltBiomeMissing " + errorAltBiomeMissing + "\n      errorAltBiomeBlock " + errorAltBiomeBlock);
+				ZLog.DevLog($"Placed all {location.m_quantity} {location.m_prefab.name} with {num12} tries in {timeSpan} ..." + "\n      errorLocationInZone " + errorLocationInZone + "\n      errorBiomeArea " + errorBiomeArea + "\n      errorCenterDistance " + errorCenterDistance + "\n      errorBiome " + errorBiome + "\n      errorAltitude " + errorAltitude + "\n      errorForest " + errorForest + "\n      errorTerrainDelta " + errorTerrainDelta + "\n      errorSimilar " + errorSimilar + "\n      errorNotSimilar " + errorNotSimilar + "\n      errorVegetation " + errorVegetation + "\n      errorAltBiomeMissing " + errorAltBiomeMissing + "\n      errorAltBiomeBlock " + errorAltBiomeBlock);
 			}
 			if (UnityEngine.Debug.isDebugBuild)
 			{
@@ -2230,7 +2230,7 @@
 			value.m_placed = true;
 			m_locationInstances[zoneID] = value;
 			TimeSpan timeSpan = DateTime.Now - now;
-			ZLog.Log($"Placed location {value.m_location.m_prefab.Name} in zone {zoneID}  duration {timeSpan.TotalMilliseconds} ms");
+			ZLog.Log($"Placed location {value.m_location.m_prefab.name} in zone {zoneID}  duration {timeSpan.TotalMilliseconds} ms");
 			if (value.m_location.m_unique)
 			{
 				RemoveUnplacedLocations(value.m_location);
@@ -2547,7 +2547,7 @@
 			{
 				array3[j].gameObject.SetActive(value: false);
 			}
-			gameObject = SoftReferenceableAssets.Utils.Instantiate(location.m_prefab, pos, rot);
+			gameObject = location.m_prefab.Instantiate(pos, rot);
 			gameObject.SetActive(value: true);
 			array = enabledComponentsInChildren3;
 			for (int j = 0; j < array.Length; j++)
@@ -2587,7 +2587,7 @@
 		GameObject gameObject = UnityEngine.Object.Instantiate(m_locationProxyPrefab, pos, rotation);
 		LocationProxy component = gameObject.GetComponent<LocationProxy>();
 		bool spawnNow = mode == SpawnMode.Full;
-		component.SetLocation(location.m_prefab.Name, seed, spawnNow);
+		component.SetLocation(location.m_prefab.name, seed, spawnNow);
 		if (mode == SpawnMode.Ghost)
 		{
 			spawnedGhostObjects.Add(gameObject);
@@ -2659,7 +2659,7 @@
 		{
 			foreach (KeyValuePair<Vector2s, LocationInstance> locationInstance in m_locationInstances)
 			{
-				if ((locationInstance.Value.m_location.m_iconAlways || (locationInstance.Value.m_location.m_iconPlaced && locationInstance.Value.m_placed)) && locationInstance.Value.m_location.m_prefab.Name == name)
+				if ((locationInstance.Value.m_location.m_iconAlways || (locationInstance.Value.m_location.m_iconPlaced && locationInstance.Value.m_placed)) && locationInstance.Value.m_location.m_prefab.name == name)
 				{
 					pos = locationInstance.Value.m_position;
 					return true;
@@ -2689,7 +2689,7 @@
 			{
 				if (value.m_location.m_iconAlways || (value.m_location.m_iconPlaced && value.m_placed))
 				{
-					icons[value.m_position] = value.m_location.m_prefab.Name;
+					icons[value.m_position] = value.m_location.m_prefab.name;
 				}
 			}
 			return;
@@ -2945,7 +2945,7 @@
 		bool result = false;
 		foreach (LocationInstance value in m_locationInstances.Values)
 		{
-			if (value.m_location.m_prefab.Name == name)
+			if (value.m_location.m_prefab.name == name)
 			{
 				float num2 = Vector3.Distance(value.m_position, point);
 				if (num2 < num)
@@ -2964,7 +2964,7 @@
 		locations.Clear();
 		foreach (LocationInstance value in m_locationInstances.Values)
 		{
-			if (value.m_location.m_prefab.Name == name)
+			if (value.m_location.m_prefab.name == name)
 			{
 				locations.Add(value);
 			}
@@ -3186,12 +3186,12 @@
 
 	public bool GetGlobalKey(GlobalKeys key, out string value)
 	{
-		return m_globalKeysValues.TryGetValue(key.ToString().ToLower(), out value);
+		return m_globalKeysValues.TryGetValue(key.ToString(), out value);
 	}
 
 	public bool GetGlobalKey(GlobalKeys key, out float value)
 	{
-		if (m_globalKeysValues.TryGetValue(key.ToString().ToLower(), out var value2) && float.TryParse(value2, NumberStyles.Any, CultureInfo.InvariantCulture, out value))
+		if (m_globalKeysValues.TryGetValue(key.ToString(), out var value2) && float.TryParse(value2, NumberStyles.Any, CultureInfo.InvariantCulture, out value))
 		{
 			return true;
 		}
@@ -3207,7 +3207,7 @@
 
 	public bool GetGlobalKey(string name, out string value)
 	{
-		return m_globalKeysValues.TryGetValue(name.ToLower(), out value);
+		return m_globalKeysValues.TryGetValue(name, out value);
 	}
 
 	public bool GetGlobalKeyExact(string fullLine)
```
