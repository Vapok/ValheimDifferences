# `Terminal.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+167/-105` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `InitTerminal() [Method Body Modified]`
- `static bool TryFixHalfAngle(float angle, out float fixedAngle)`

---

## 📝 Code Diff

```diff
--- a/Terminal.cs
+++ b/Terminal.cs
@@ -523,6 +523,56 @@
 				ZoneSystem.instance.GenerateLocations();
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
+		new ConsoleCommand("fixHalfDegRotPieces", "Fixes rotation of all nearby Pieces saved at up to half a degree wrong, which was a problem between 1.0.0 and 1.0.21. Use at your own risk!", (ConsoleEventArgs args) =>
+		{
+			List<Piece> list = new List<Piece>();
+			Piece.GetAllPiecesInRadius(Player.m_localPlayer.transform.position, 9999f, list);
+			StringBuilder stringBuilder = new StringBuilder();
+			StringBuilder stringBuilder2 = new StringBuilder();
+			int num2 = 0;
+			int num3 = 0;
+			foreach (Piece item3 in list)
+			{
+				Vector3 eulerAngles = item3.transform.rotation.eulerAngles;
+				Vector3 vector = eulerAngles;
+				bool flag = false;
+				if (TryFixHalfAngle(eulerAngles.x, out var fixedAngle))
+				{
+					eulerAngles.x = fixedAngle;
+					flag = true;
+				}
+				if (TryFixHalfAngle(eulerAngles.y, out var fixedAngle2))
+				{
+					eulerAngles.y = fixedAngle2;
+					flag = true;
+				}
+				if (TryFixHalfAngle(eulerAngles.z, out var fixedAngle3))
+				{
+					eulerAngles.z = fixedAngle3;
+					flag = true;
+				}
+				if (flag)
+				{
+					ZNetView component = item3.GetComponent<ZNetView>();
+					if (component != null && component.IsOwner())
+					{
+						stringBuilder.AppendLine(item3.name + ": " + vector.ToString("G9") + " -> " + eulerAngles.ToString("G9"));
+						num2++;
+						Quaternion rotation = Quaternion.Euler(eulerAngles);
+						item3.transform.rotation = rotation;
+						component.GetZDO().SetRotation(rotation);
+					}
+					else
+					{
+						num3++;
+						stringBuilder2.AppendLine("Wanted to change " + item3.name + " from " + vector.ToString("G9") + " -> " + eulerAngles.ToString("G9") + ", but was not owner or too far away!");
+					}
+				}
+			}
+			args.Context.AddString($"Fixed {num2} pieces, failed to fix {num3} pieces. See player.log for details.");
+			ZLog.Log($"Fixed {num2} pieces:\n{stringBuilder}");
+			ZLog.Log($"Failed to fix {num3}:\n{stringBuilder2}");
+		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, null, alwaysRefreshTabOptions: false, remoteCommand: true);
 		new ConsoleCommand("players", "[nr] - force diffuculty scale ( 0 = reset)", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
@@ -646,9 +696,9 @@
 		{
 			List<string> globalKeys = ZoneSystem.instance.GetGlobalKeys();
 			args.Context.AddString($"Current Keys: {globalKeys.Count}");
-			foreach (string item3 in globalKeys)
-			{
-				args.Context.AddString("  " + item3);
+			foreach (string item4 in globalKeys)
+			{
+				args.Context.AddString("  " + item4);
 			}
 			args.Context.AddString($"Server Option Keys: {ZNet.World.m_startingGlobalKeys.Count}");
 			foreach (string startingGlobalKey in ZNet.World.m_startingGlobalKeys)
@@ -672,9 +722,9 @@
 			{
 				globalKeys = Player.m_localPlayer.GetUniqueKeys();
 				args.Context.AddString($"Player Keys: {globalKeys.Count}");
-				foreach (string item4 in globalKeys)
-				{
-					args.Context.AddString("  " + item4);
+				foreach (string item5 in globalKeys)
+				{
+					args.Context.AddString("  " + item5);
 				}
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
@@ -762,6 +812,7 @@
 			{
 				PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
 				args.Context.AddString("Player stats");
+				args.Context.AddString("Created: " + Game.instance.GetPlayerProfile().m_dateCreated.ToString("yyyy-MM-dd HH:mm:ss"));
 				if (playerProfile.m_usedCheats)
 				{
 					args.Context.AddString("Cheater!");
@@ -789,9 +840,9 @@
 					for (int j = 0; j < 5; j++)
 					{
 						args.Context.AddString($" {(KillModifiers)j}:");
-						foreach (KeyValuePair<string, float> item5 in playerProfile.m_playerStats[i].m_enemyStats[j])
+						foreach (KeyValuePair<string, float> item6 in playerProfile.m_playerStats[i].m_enemyStats[j])
 						{
-							args.Context.AddString($"  {Localization.instance.Localize(item5.Key)}: {item5.Value}");
+							args.Context.AddString($"  {Localization.instance.Localize(item6.Key)}: {item6.Value}");
 						}
 					}
 					args.Context.AddString("Items found:");
@@ -1050,28 +1101,28 @@
 			GetInfo(Character.GetAllCharacters());
 			GetInfo(UnityEngine.Object.FindObjectsOfType<RandomFlyingBird>());
 			GetInfo(UnityEngine.Object.FindObjectsOfType<Fish>());
-			foreach (KeyValuePair<string, Dictionary<int, int>> item6 in counts)
-			{
-				string text = Localization.instance.Localize(item6.Key) + ": ";
-				foreach (KeyValuePair<int, int> item7 in item6.Value)
-				{
-					text += $"Level {item7.Key}: {item7.Value}, ";
+			foreach (KeyValuePair<string, Dictionary<int, int>> item7 in counts)
+			{
+				string text = Localization.instance.Localize(item7.Key) + ": ";
+				foreach (KeyValuePair<int, int> item8 in item7.Value)
+				{
+					text += $"Level {item8.Key}: {item8.Value}, ";
 				}
 				args.Context.AddString(text);
 			}
 			void GetInfo(IEnumerable collection)
 			{
-				foreach (object item8 in collection)
-				{
-					if (item8 is Character character)
+				foreach (object item9 in collection)
+				{
+					if (item9 is Character character)
 					{
 						count(character.m_name, character.GetLevel());
 					}
-					else if (item8 is RandomFlyingBird)
+					else if (item9 is RandomFlyingBird)
 					{
 						count("Bird", 1);
 					}
-					else if (item8 is Fish fish)
+					else if (item9 is Fish fish)
 					{
 						ItemDrop component = fish.GetComponent<ItemDrop>();
 						if ((object)component != null)
@@ -1080,9 +1131,9 @@
 						}
 					}
 				}
-				foreach (object item9 in collection)
-				{
-					if (item9 is MonoBehaviour monoBehaviour)
+				foreach (object item10 in collection)
+				{
+					if (item10 is MonoBehaviour monoBehaviour)
 					{
 						args.Context.AddString(string.Format("   {0}, Dist: {1}, Offset: {2}", monoBehaviour.name, Vector3.Distance(Player.m_localPlayer.transform.position, monoBehaviour.transform.position).ToString("0.0"), monoBehaviour.transform.position - Player.m_localPlayer.transform.position));
 					}
@@ -1129,9 +1180,9 @@
 				}
 			}
 			args.Context.AddString($"Total network objects found: {total}");
-			foreach (KeyValuePair<string, int> item10 in counts)
-			{
-				args.Context.AddString($"   {item10.Key}: {item10.Value}");
+			foreach (KeyValuePair<string, int> item11 in counts)
+			{
+				args.Context.AddString($"   {item11.Key}: {item11.Value}");
 			}
 			void add(string key)
 			{
@@ -1179,11 +1230,11 @@
 			string text = args[1].ToLower();
 			List<Tuple<object, Vector3>> list = find(text);
 			list.Sort((Tuple<object, Vector3> a, Tuple<object, Vector3> b) => Vector3.Distance(a.Item2, Player.m_localPlayer.transform.position).CompareTo(Vector3.Distance(b.Item2, Player.m_localPlayer.transform.position)));
-			foreach (Tuple<object, Vector3> item11 in list)
+			foreach (Tuple<object, Vector3> item12 in list)
 			{
 				Terminal context = args.Context;
-				string arg = ((item11.Item1 is GameObject gameObject) ? gameObject.name.ToString() : ((item11.Item1 is ZoneSystem.LocationInstance locationInstance) ? locationInstance.m_location.m_prefab.Name : "unknown"));
-				context.AddString(string.Format("   {0}, Dist: {1}, Pos: {2}", arg, Vector3.Distance(Player.m_localPlayer.transform.position, item11.Item2).ToString("0.0"), item11.Item2));
+				string arg = ((item12.Item1 is GameObject gameObject) ? gameObject.name.ToString() : ((item12.Item1 is ZoneSystem.LocationInstance locationInstance) ? locationInstance.m_location.m_prefab.name : "unknown"));
+				context.AddString(string.Format("   {0}, Dist: {1}, Pos: {2}", arg, Vector3.Distance(Player.m_localPlayer.transform.position, item12.Item2).ToString("0.0"), item12.Item2));
 			}
 			foreach (Minimap.PinData findPin in args.Context.m_findPins)
 			{
@@ -1296,7 +1347,7 @@
 			{
 				if (location2.m_prefab.IsValid)
 				{
-					list.Add(location2.m_prefab.Name);
+					list.Add(location2.m_prefab.name);
 				}
 			}
 			return list;
@@ -1315,27 +1366,27 @@
 			}
 			Vector3 p = Player.m_localPlayer.transform.position + Player.m_localPlayer.transform.forward * 2f;
 			string text = args[1].ToLower();
-			foreach (ZoneSystem.ZoneVegetation item12 in ZoneSystem.instance.m_vegetation)
-			{
-				if (item12.m_prefab.name.ToLower() == text)
+			foreach (ZoneSystem.ZoneVegetation item13 in ZoneSystem.instance.m_vegetation)
+			{
+				if (item13.m_prefab.name.ToLower() == text)
 				{
 					float y = UnityEngine.Random.Range(0, 360);
-					float num2 = UnityEngine.Random.Range(item12.m_scaleMin, item12.m_scaleMax);
-					float x = UnityEngine.Random.Range(0f - item12.m_randTilt, item12.m_randTilt);
-					float z = UnityEngine.Random.Range(0f - item12.m_randTilt, item12.m_randTilt);
+					float num2 = UnityEngine.Random.Range(item13.m_scaleMin, item13.m_scaleMax);
+					float x = UnityEngine.Random.Range(0f - item13.m_randTilt, item13.m_randTilt);
+					float z = UnityEngine.Random.Range(0f - item13.m_randTilt, item13.m_randTilt);
 					ZoneSystem.instance.GetGroundData(ref p, out var normal, out var _, out var _, out var _);
-					if (item12.m_snapToStaticSolid && ZoneSystem.instance.GetStaticSolidHeight(p, out var height, out var normal2))
+					if (item13.m_snapToStaticSolid && ZoneSystem.instance.GetStaticSolidHeight(p, out var height, out var normal2))
 					{
 						p.y = height;
 						normal = normal2;
 					}
-					if (item12.m_snapToWater)
+					if (item13.m_snapToWater)
 					{
 						p.y = 30f;
 					}
-					p.y += item12.m_groundOffset;
+					p.y += item13.m_groundOffset;
 					Quaternion identity = Quaternion.identity;
-					if (item12.m_chanceToUseGroundTilt > 0f && UnityEngine.Random.value <= item12.m_chanceToUseGroundTilt)
+					if (item13.m_chanceToUseGroundTilt > 0f && UnityEngine.Random.value <= item13.m_chanceToUseGroundTilt)
 					{
 						Quaternion quaternion = Quaternion.Euler(0f, y, 0f);
 						identity = Quaternion.LookRotation(Vector3.Cross(normal, quaternion * Vector3.forward), normal);
@@ -1344,7 +1395,7 @@
 					{
 						identity = Quaternion.Euler(x, y, z);
 					}
-					GameObject gameObject = UnityEngine.Object.Instantiate(item12.m_prefab, p, identity);
+					GameObject gameObject = UnityEngine.Object.Instantiate(item13.m_prefab, p, identity);
 					gameObject.GetComponent<ZNetView>().SetLocalScale(new Vector3(num2, num2, num2));
 					Collider[] componentsInChildren = gameObject.GetComponentsInChildren<Collider>();
 					foreach (Collider obj in componentsInChildren)
@@ -1359,11 +1410,11 @@
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
-			foreach (ZoneSystem.ZoneVegetation item13 in ZoneSystem.instance.m_vegetation)
-			{
-				if (item13.m_prefab != null)
-				{
-					list.Add(item13.m_prefab.name);
+			foreach (ZoneSystem.ZoneVegetation item14 in ZoneSystem.instance.m_vegetation)
+			{
+				if (item14.m_prefab != null)
+				{
+					list.Add(item14.m_prefab.name);
 				}
 			}
 			return list;
@@ -1478,29 +1529,29 @@
 							if (vals != null)
 							{
 								component.GetZDO().Set("HasFields", value: true);
-								foreach (KeyValuePair<string, object> item14 in vals)
+								foreach (KeyValuePair<string, object> item15 in vals)
 								{
-									string[] array3 = item14.Key.Split('.');
+									string[] array3 = item15.Key.Split('.');
 									if (array3.Length >= 2)
 									{
 										("HasFields" + array3[0]).GetStableHashCode();
 										component.GetZDO().Set("HasFields" + array3[0], value: true);
-										item14.Value.GetType();
-										if (item14.Value is float)
+										item15.Value.GetType();
+										if (item15.Value is float)
 										{
-											component.GetZDO().Set(item14.Key, (float)item14.Value);
+											component.GetZDO().Set(item15.Key, (float)item15.Value);
 										}
-										else if (item14.Value is int)
+										else if (item15.Value is int)
 										{
-											component.GetZDO().Set(item14.Key, (int)item14.Value);
+											component.GetZDO().Set(item15.Key, (int)item15.Value);
 										}
-										else if (item14.Value is bool)
+										else if (item15.Value is bool)
 										{
-											component.GetZDO().Set(item14.Key, (bool)item14.Value);
+											component.GetZDO().Set(item15.Key, (bool)item15.Value);
 										}
 										else
 										{
-											component.GetZDO().Set(item14.Key, item14.Value.ToString());
+											component.GetZDO().Set(item15.Key, item15.Value.ToString());
 										}
 									}
 								}
@@ -1674,11 +1725,11 @@
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
 			int num3 = 0;
-			foreach (Character item15 in allCharacters)
-			{
-				if (ShouldKillAll(item15, killTamed: true))
-				{
-					item15.Damage(new HitData(1E+10f));
+			foreach (Character item16 in allCharacters)
+			{
+				if (ShouldKillAll(item16, killTamed: true))
+				{
+					item16.Damage(new HitData(1E+10f));
 					num2++;
 				}
 			}
@@ -1698,11 +1749,11 @@
 		{
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
-			foreach (Character item16 in allCharacters)
-			{
-				if (ShouldKillAll(item16))
-				{
-					item16.Damage(new HitData(1E+10f));
+			foreach (Character item17 in allCharacters)
+			{
+				if (ShouldKillAll(item17))
+				{
+					item17.Damage(new HitData(1E+10f));
 					num2++;
 				}
 			}
@@ -1713,11 +1764,11 @@
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
 			int num3 = 0;
-			foreach (Character item17 in allCharacters)
-			{
-				if (ShouldKillAll(item17))
-				{
-					item17.Damage(new HitData(1E+10f));
+			foreach (Character item18 in allCharacters)
+			{
+				if (ShouldKillAll(item18))
+				{
+					item18.Damage(new HitData(1E+10f));
 					num2++;
 				}
 			}
@@ -1737,11 +1788,11 @@
 		{
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
-			foreach (Character item18 in allCharacters)
-			{
-				if (ShouldKillAll(item18, killTamed: true))
-				{
-					item18.Damage(new HitData
+			foreach (Character item19 in allCharacters)
+			{
+				if (ShouldKillAll(item19, killTamed: true))
+				{
+					item19.Damage(new HitData
 					{
 						m_damage = 
 						{
@@ -2032,9 +2083,9 @@
 		{
 			List<StatusEffect> statusEffects = ObjectDB.instance.m_StatusEffects;
 			List<string> list = new List<string>();
-			foreach (StatusEffect item19 in statusEffects)
-			{
-				list.Add(item19.name);
+			foreach (StatusEffect item20 in statusEffects)
+			{
+				list.Add(item20.name);
 			}
 			return list;
 		}, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
@@ -2051,9 +2102,9 @@
 		{
 			List<StatusEffect> statusEffects = ObjectDB.instance.m_StatusEffects;
 			List<string> list = new List<string>();
-			foreach (StatusEffect item20 in statusEffects)
-			{
-				list.Add(item20.name);
+			foreach (StatusEffect item21 in statusEffects)
+			{
+				list.Add(item21.name);
 			}
 			return list;
 		}, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
@@ -2177,9 +2228,9 @@
 					return;
 				}
 				args.Context.AddString("Current events:");
-				foreach (PersistentEventSystem.ActivePersistentEvent item21 in activePersistentEvents.list)
-				{
-					args.Context.AddString($"{item21.eventId}: {item21.internalName} | Position: {item21.position}");
+				foreach (PersistentEventSystem.ActivePersistentEvent item22 in activePersistentEvents.list)
+				{
+					args.Context.AddString($"{item22.eventId}: {item22.internalName} | Position: {item22.position}");
 				}
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
@@ -2304,9 +2355,9 @@
 			}
 			List<ItemDrop.ItemData> list = new List<ItemDrop.ItemData>();
 			Player.m_localPlayer.GetInventory().GetWornItems(list);
-			foreach (ItemDrop.ItemData item22 in list)
-			{
-				item22.m_durability = item22.GetMaxDurability();
+			foreach (ItemDrop.ItemData item23 in list)
+			{
+				item23.m_durability = item23.GetMaxDurability();
 			}
 			return true;
 		}, isCheat: true);
@@ -2473,19 +2524,19 @@
 			args.Context.AddString("Modifiers will only appear in unexplored zones.");
 			args.Context.AddString($"AltBiome modifiers total: {AltBiomeList.m_altBiomes.Count}");
 			dictionary.Clear();
-			foreach (KeyValuePair<Heightmap.Biome, int> item23 in dictionary)
+			foreach (KeyValuePair<Heightmap.Biome, int> item24 in dictionary)
 			{
 				foreach (AltBiome altBiome in AltBiomeList.m_altBiomes)
 				{
-					if (altBiome.m_biome.HasFlag(item23.Key))
-					{
-						dictionary[item23.Key] = item23.Value + 1;
-					}
-				}
-			}
-			foreach (KeyValuePair<Heightmap.Biome, int> item24 in dictionary)
-			{
-				args.Context.AddString($"   {item24.Key}: {item24.Value}\n");
+					if (altBiome.m_biome.HasFlag(item24.Key))
+					{
+						dictionary[item24.Key] = item24.Value + 1;
+					}
+				}
+			}
+			foreach (KeyValuePair<Heightmap.Biome, int> item25 in dictionary)
+			{
+				args.Context.AddString($"   {item25.Key}: {item25.Value}\n");
 			}
 			if (biomeData.groupTex != null)
 			{
@@ -2532,9 +2583,9 @@
 				}
 			}
 			list.Sort((BiomeSector a, BiomeSector b) => Vector3.Distance(a.Center, Player.m_localPlayer.transform.position).CompareTo(Vector3.Distance(b.Center, Player.m_localPlayer.transform.position)));
-			foreach (BiomeSector item25 in list)
-			{
-				args.Context.AddString($"   {item25}");
+			foreach (BiomeSector item26 in list)
+			{
+				args.Context.AddString($"   {item26}");
 			}
 			foreach (Minimap.PinData findPin2 in args.Context.m_findPins)
 			{
@@ -2652,6 +2703,17 @@
 				return false;
 			}
 			return true;
+		}
+		static bool TryFixHalfAngle(float angle, out float fixedAngle)
+		{
+			float num2 = (angle + 0.5f) / 22.5f;
+			if (Mathf.Abs(num2 - Mathf.Round(num2)) < 0.001f)
+			{
+				fixedAngle = Mathf.Round(num2) * 22.5f % 360f;
+				return true;
+			}
+			fixedAngle = angle;
+			return false;
 		}
 		static List<Tuple<object, Vector3>> find(string q)
 		{
@@ -2668,7 +2730,7 @@
 			}
 			foreach (ZoneSystem.LocationInstance location3 in ZoneSystem.instance.GetLocationList())
 			{
-				if (location3.m_location.m_prefab.Name.ToLower().Contains(q))
+				if (location3.m_location.m_prefab.name.ToLower().Contains(q))
 				{
 					list.Add(new Tuple<object, Vector3>(location3, location3.m_position));
 				}
@@ -2678,9 +2740,9 @@
 			while (!ZDOMan.instance.GetAllZDOsWithPrefabIterative(q, list2, ref index))
 			{
 			}
-			foreach (ZDO item26 in list2)
-			{
-				list.Add(new Tuple<object, Vector3>(item26, item26.GetPosition()));
+			foreach (ZDO item27 in list2)
+			{
+				list.Add(new Tuple<object, Vector3>(item27, item27.GetPosition()));
 			}
 			return list;
 		}
@@ -2695,7 +2757,7 @@
 			{
 				if (location4.m_enable || location4.m_prefab.IsValid)
 				{
-					list.Add(location4.m_prefab.Name);
+					list.Add(location4.m_prefab.name);
 				}
 			}
 			return list;
```
