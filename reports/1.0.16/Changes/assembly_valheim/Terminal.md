# `Terminal.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+198/-188` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Terminal.cs
+++ b/Terminal.cs
@@ -342,7 +342,7 @@
 		}
 		m_terminalInitialized = true;
 		AddConsoleCheatCommands();
-		new ConsoleCommand("help", "Shows a list of console commands (optional: help 2 4 shows the second quarter)", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("help", "Shows a list of console commands (optional: help 2 4 shows the second quarter)", (ConsoleEventArgs args) =>
 		{
 			if ((bool)ZNet.instance && ZNet.instance.IsServer())
 			{
@@ -378,7 +378,7 @@
 				}
 			}
 		});
-		new ConsoleCommand("devcommands", "enables cheats", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("devcommands", "enables cheats", (ConsoleEventArgs args) =>
 		{
 			if ((bool)ZNet.instance && !ZNet.instance.IsServer())
 			{
@@ -393,30 +393,30 @@
 			Gogan.LogEvent("Cheat", "CheatsEnabled", m_cheat.ToString(), 0L);
 			args.Context.updateCommandList();
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: true);
-		new ConsoleCommand("confirmcheats", "", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("confirmcheats", "", (ConsoleEventArgs args) =>
 		{
 			args.Context?.AddString(Localization.instance.Localize("$achievements_permanently_cheated_character"));
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: true, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("hidebetatext", "", delegate
+		new ConsoleCommand("hidebetatext", "", (ConsoleEventArgs args) =>
 		{
 			if ((bool)Hud.instance)
 			{
 				Hud.instance.ToggleBetaTextVisible();
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: true);
-		new ConsoleCommand("ping", "ping server", delegate
+		new ConsoleCommand("ping", "ping server", (ConsoleEventArgs args) =>
 		{
 			if ((bool)Game.instance)
 			{
 				Game.instance.Ping();
 			}
 		});
-		new ConsoleCommand("dpsdebug", "toggle dps debug print", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("dpsdebug", "toggle dps debug print", (ConsoleEventArgs args) =>
 		{
 			Character.SetDPSDebug(!Character.IsDPSDebugEnabled());
 			args.Context?.AddString("DPS debug " + Character.IsDPSDebugEnabled());
 		}, isCheat: true);
-		new ConsoleCommand("lodbias", "set distance lod bias", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("lodbias", "set distance lod bias", (ConsoleEventArgs args) =>
 		{
 			float value;
 			if (args.Length == 1)
@@ -429,13 +429,13 @@
 				QualitySettings.lodBias = value;
 			}
 		});
-		new ConsoleCommand("info", "print system info", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("info", "print system info", (ConsoleEventArgs args) =>
 		{
 			args.Context.AddString("Render threading mode:" + SystemInfo.renderingThreadingMode);
 			long totalMemory = GC.GetTotalMemory(forceFullCollection: false);
 			args.Context.AddString("Total allocated mem: " + (totalMemory / 1048576).ToString("0") + "mb");
 		});
-		new ConsoleCommand("gc", "shows garbage collector information", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("gc", "shows garbage collector information", (ConsoleEventArgs args) =>
 		{
 			long totalMemory = GC.GetTotalMemory(forceFullCollection: false);
 			GC.Collect();
@@ -443,12 +443,12 @@
 			long num2 = totalMemory2 - totalMemory;
 			args.Context.AddString("GC collect, Delta: " + (num2 / 1048576).ToString("0") + "mb   Total left:" + (totalMemory2 / 1048576).ToString("0") + "mb");
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("cr", "unloads unused assets", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("cr", "unloads unused assets", (ConsoleEventArgs args) =>
 		{
 			args.Context.AddString("Unloading unused assets");
 			Game.instance.CollectResources(displayMessage: true);
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("fov", "changes camera field of view", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("fov", "changes camera field of view", (ConsoleEventArgs args) =>
 		{
 			Camera mainCamera = Utils.GetMainCamera();
 			if ((bool)mainCamera)
@@ -469,7 +469,7 @@
 				}
 			}
 		});
-		new ConsoleCommand("kick", "[name/ip/userID] - kick user", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("kick", "[name/ip/userID] - kick user", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -479,7 +479,7 @@
 			ZNet.instance.Kick(user);
 			return true;
 		}, isCheat: false, isNetwork: true);
-		new ConsoleCommand("ban", "[name/ip/userID] - ban user", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("ban", "[name/ip/userID] - ban user", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -489,7 +489,7 @@
 			ZNet.instance.Ban(user);
 			return true;
 		}, isCheat: false, isNetwork: true);
-		new ConsoleCommand("unban", "[ip/userID] - unban user", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("unban", "[ip/userID] - unban user", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -499,20 +499,20 @@
 			ZNet.instance.Unban(user);
 			return true;
 		}, isCheat: false, isNetwork: true);
-		new ConsoleCommand("banned", "list banned users", delegate
+		new ConsoleCommand("banned", "list banned users", (ConsoleEventArgs args) =>
 		{
 			ZNet.instance.PrintBanned();
 		}, isCheat: false, isNetwork: true);
-		new ConsoleCommand("save", "force saving of world and resets world save interval", delegate
+		new ConsoleCommand("save", "force saving of world and resets world save interval", (ConsoleEventArgs args) =>
 		{
 			ZNet.instance.SaveWorldAndPlayerProfiles();
 		}, isCheat: false, isNetwork: true);
-		new ConsoleCommand("optterrain", "optimize old terrain modifications", delegate
+		new ConsoleCommand("optterrain", "optimize old terrain modifications", (ConsoleEventArgs args) =>
 		{
 			TerrainComp.UpgradeTerrain();
 			Heightmap.UpdateTerrainAlpha();
 		}, isCheat: false, isNetwork: true);
-		new ConsoleCommand("genloc", "regenerate all locations.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("genloc", "regenerate all locations.", (ConsoleEventArgs args) =>
 		{
 			if (args.Length >= 2 && args[1].ToLower() == "alt")
 			{
@@ -523,7 +523,7 @@
 				ZoneSystem.instance.GenerateLocations();
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("players", "[nr] - force diffuculty scale ( 0 = reset)", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("players", "[nr] - force diffuculty scale ( 0 = reset)", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -536,7 +536,7 @@
 			}
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("exclusivefullscreen", "changes window mode to exclusive fullscreen, or back to borderless", delegate
+		new ConsoleCommand("exclusivefullscreen", "changes window mode to exclusive fullscreen, or back to borderless", (ConsoleEventArgs args) =>
 		{
 			if (Screen.fullScreenMode != FullScreenMode.ExclusiveFullScreen)
 			{
@@ -547,7 +547,7 @@
 				Screen.fullScreenMode = FullScreenMode.FullScreenWindow;
 			}
 		});
-		new ConsoleCommand("setkey", "[name]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("setkey", "[name]", (ConsoleEventArgs args) =>
 		{
 			if (args.Length >= 2)
 			{
@@ -566,13 +566,13 @@
 			{
 				args.Context.AddString("Syntax: setkey [key]");
 			}
-		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, delegate
+		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, () =>
 		{
 			List<string> list = Enum.GetNames(typeof(GlobalKeys)).ToList();
 			list.Remove(GlobalKeys.NonServerOption.ToString());
 			return list;
 		}, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("removekey", "[name]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("removekey", "[name]", (ConsoleEventArgs args) =>
 		{
 			if (args.Length >= 2)
 			{
@@ -584,18 +584,18 @@
 				args.Context.AddString("Syntax: setkey [key]");
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, () => (!ZoneSystem.instance) ? null : ZoneSystem.instance.GetGlobalKeys(), alwaysRefreshTabOptions: true, remoteCommand: true);
-		new ConsoleCommand("resetkeys", "[name]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetkeys", "[name]", (ConsoleEventArgs args) =>
 		{
 			ZoneSystem.instance.ResetGlobalKeys();
 			Player.m_localPlayer?.ResetUniqueKeys();
 			args.Context.AddString("Global and player keys cleared");
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("resetworldkeys", "[name] Resets all world modifiers to default", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetworldkeys", "[name] Resets all world modifiers to default", (ConsoleEventArgs args) =>
 		{
 			ZoneSystem.instance.ResetWorldKeys();
 			args.Context.AddString("Server keys cleared");
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("setworldpreset", "[name] Resets all world modifiers to a named preset", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("setworldpreset", "[name] Resets all world modifiers to a named preset", (ConsoleEventArgs args) =>
 		{
 			if (!Enum.TryParse<WorldPresets>(args[1], ignoreCase: true, out var result))
 			{
@@ -607,7 +607,7 @@
 			ServerOptionsGUI.m_instance.SetKeys(ZNet.World);
 			return true;
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => Enum.GetNames(typeof(WorldPresets)).ToList(), alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("setworldmodifier", "[name] [value] Sets a world modifier value", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("setworldmodifier", "[name] [value] Sets a world modifier value", (ConsoleEventArgs args) =>
 		{
 			if (!Enum.TryParse<WorldModifiers>(args[1], ignoreCase: true, out var result) || !Enum.TryParse<WorldModifierOption>(args[2], ignoreCase: true, out var result2))
 			{
@@ -618,7 +618,7 @@
 			ServerOptionsGUI.m_instance.SetKeys(ZNet.World);
 			return true;
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => Enum.GetNames(typeof(WorldModifiers)).ToList(), alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("setkeyplayer", "[name]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("setkeyplayer", "[name]", (ConsoleEventArgs args) =>
 		{
 			if (args.Length >= 2)
 			{
@@ -630,7 +630,7 @@
 				args.Context.AddString("Syntax: setkey [key]");
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => Enum.GetNames(typeof(PlayerKeys)).ToList());
-		new ConsoleCommand("removekeyplayer", "[name]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("removekeyplayer", "[name]", (ConsoleEventArgs args) =>
 		{
 			if (args.Length >= 2)
 			{
@@ -642,7 +642,7 @@
 				args.Context.AddString("Syntax: setkey [key]");
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => (!Player.m_localPlayer) ? null : Player.m_localPlayer.GetUniqueKeys(), alwaysRefreshTabOptions: true);
-		new ConsoleCommand("listkeys", "", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("listkeys", "", (ConsoleEventArgs args) =>
 		{
 			List<string> globalKeys = ZoneSystem.instance.GetGlobalKeys();
 			args.Context.AddString($"Current Keys: {globalKeys.Count}");
@@ -678,7 +678,7 @@
 				}
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("sortcraft", "[type] sorts crafting lists according to setting", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("sortcraft", "[type] sorts crafting lists according to setting", (ConsoleEventArgs args) =>
 		{
 			Player.m_localPlayer.RemoveUniqueKeyValue("sortcraft");
 			if (args.Length >= 2 && args[1].Length > 0)
@@ -691,12 +691,12 @@
 				args.Context.AddString("List sorting reset");
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => Enum.GetNames(typeof(InventoryGui.SortMethod)).ToList());
-		new ConsoleCommand("debugmode", "fly mode", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("debugmode", "fly mode", (ConsoleEventArgs args) =>
 		{
 			Player.m_debugMode = !Player.m_debugMode;
 			args.Context.AddString("Debugmode " + Player.m_debugMode);
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("fly", "fly mode", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("fly", "fly mode", (ConsoleEventArgs args) =>
 		{
 			Player.m_localPlayer.ToggleDebugFly();
 			if (args.TryParameterInt(1, out var value))
@@ -704,7 +704,7 @@
 				Character.m_debugFlySpeed = value;
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("nocost", "no build cost", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("nocost", "no build cost", (ConsoleEventArgs args) =>
 		{
 			if (args.HasArgumentAnywhere("on"))
 			{
@@ -719,7 +719,7 @@
 				Player.m_localPlayer.ToggleNoPlacementCost();
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("raiseskill", "[skill] [amount]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("raiseskill", "[skill] [amount]", (ConsoleEventArgs args) =>
 		{
 			if (args.TryParameterInt(2, out var value))
 			{
@@ -729,13 +729,13 @@
 			{
 				args.Context.AddString("Syntax: raiseskill [skill] [amount]");
 			}
-		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = Enum.GetNames(typeof(Skills.SkillType)).ToList();
 			list.Remove(Skills.SkillType.None.ToString());
 			return list;
 		});
-		new ConsoleCommand("resetskill", "[skill]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetskill", "[skill]", (ConsoleEventArgs args) =>
 		{
 			if (args.Length > 1)
 			{
@@ -746,17 +746,17 @@
 			{
 				args.Context.AddString("Syntax: resetskill [skill]");
 			}
-		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = Enum.GetNames(typeof(Skills.SkillType)).ToList();
 			list.Remove(Skills.SkillType.None.ToString());
 			return list;
 		});
-		new ConsoleCommand("sleep", "skips to next morning", delegate
+		new ConsoleCommand("sleep", "skips to next morning", (ConsoleEventArgs args) =>
 		{
 			EnvMan.instance.SkipToMorning();
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("stats", "shows player stats", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("stats", "shows player stats", (ConsoleEventArgs args) =>
 		{
 			if ((bool)Game.instance)
 			{
@@ -825,7 +825,7 @@
 				}
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("achievements", "shows player achievement info", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("achievements", "shows player achievement info", (ConsoleEventArgs args) =>
 		{
 			if ((bool)Game.instance)
 			{
@@ -885,7 +885,7 @@
 				}
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("yesiuseddevcommandsbutiwantmyachievementsanyway", "[1 = true/ 0 = false] Normally cheated items / pieces don't trigger achievements. Turn this on to disable cheat checks.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("yesiuseddevcommandsbutiwantmyachievementsanyway", "[1 = true/ 0 = false] Normally cheated items / pieces don't trigger achievements. Turn this on to disable cheat checks.", (ConsoleEventArgs args) =>
 		{
 			Player localPlayer = Player.m_localPlayer;
 			if (!(localPlayer == null))
@@ -908,7 +908,7 @@
 				}
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: true);
-		new ConsoleCommand("getstat", "get specific stat", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("getstat", "get specific stat", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -920,7 +920,7 @@
 				return true;
 			}
 			PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
-			PlatformManager.DistributionPlatform?.AchievementManager.GetProgress(stat.ToString(), delegate(bool success, float progress)
+			PlatformManager.DistributionPlatform?.AchievementManager.GetProgress(stat.ToString(), (bool success, float progress) =>
 			{
 				args.Context.AddString($"{stat}: remote: {progress}");
 			});
@@ -930,7 +930,7 @@
 			}
 			return true;
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => Enum.GetNames(typeof(PlayerStatType)).ToList());
-		new ConsoleCommand("skiptime", "[gameseconds] skips head in seconds", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("skiptime", "[gameseconds] skips head in seconds", (ConsoleEventArgs args) =>
 		{
 			double timeSeconds = ZNet.instance.GetTimeSeconds();
 			float num2 = args.TryParameterFloat(1, 240f);
@@ -938,13 +938,13 @@
 			ZNet.instance.SetNetTime(timeSeconds);
 			args.Context.AddString("Skipping " + num2.ToString("0") + "s , Day:" + EnvMan.instance.GetDay(timeSeconds));
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("time", "shows current time", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("time", "shows current time", (ConsoleEventArgs args) =>
 		{
 			double timeSeconds = ZNet.instance.GetTimeSeconds();
 			bool flag = EnvMan.CanSleep();
 			args.Context.AddString(string.Format("{0} sec, Day: {1} ({2}), {3}, Session start: {4}", timeSeconds.ToString("0.00"), EnvMan.instance.GetDay(timeSeconds), EnvMan.instance.GetDayFraction().ToString("0.00"), flag ? "Can sleep" : "Can NOT sleep", ZoneSystem.instance.TimeSinceStart()));
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("maxfps", "[FPS] sets fps limit", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("maxfps", "[FPS] sets fps limit", (ConsoleEventArgs args) =>
 		{
 			if (args.TryParameterInt(1, out var value))
 			{
@@ -955,22 +955,22 @@
 			}
 			return false;
 		});
-		new ConsoleCommand("resetcharacter", "reset character data", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetcharacter", "reset character data", (ConsoleEventArgs args) =>
 		{
 			args.Context?.AddString("Reseting character");
 			Player.m_localPlayer.ResetCharacter();
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("resetknownitems", "reset character known items & recipes", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetknownitems", "reset character known items & recipes", (ConsoleEventArgs args) =>
 		{
 			args.Context?.AddString("Reseting known items for character");
 			Player.m_localPlayer.ResetCharacterKnownItems();
 		});
-		new ConsoleCommand("tutorialreset", "reset tutorial data", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("tutorialreset", "reset tutorial data", (ConsoleEventArgs args) =>
 		{
 			args.Context?.AddString("Reseting tutorials");
 			Player.ResetSeenTutorials();
 		});
-		new ConsoleCommand("timescale", "[target] [fadetime, default: 1, max: 3] sets timescale", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("timescale", "[target] [fadetime, default: 1, max: 3] sets timescale", (ConsoleEventArgs args) =>
 		{
 			if (args.TryParameterFloat(1, out var value))
 			{
@@ -979,11 +979,11 @@
 			}
 			return false;
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("randomevent", "start a random event", delegate
+		new ConsoleCommand("randomevent", "start a random event", (ConsoleEventArgs args) =>
 		{
 			RandEventSystem.instance.StartRandomEvent();
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("event", "[name] - start event", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("event", "[name] - start event", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -997,7 +997,7 @@
 			}
 			RandEventSystem.instance.SetRandomEventByName(text, Player.m_localPlayer.transform.position);
 			return true;
-		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			foreach (RandomEvent @event in RandEventSystem.instance.m_events)
@@ -1006,11 +1006,11 @@
 			}
 			return list;
 		});
-		new ConsoleCommand("stopevent", "stop current event", delegate
+		new ConsoleCommand("stopevent", "stop current event", (ConsoleEventArgs args) =>
 		{
 			RandEventSystem.instance.ResetRandomEvent();
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("removedrops", "remove all item-drops in area", delegate
+		new ConsoleCommand("removedrops", "remove all item-drops in area", (ConsoleEventArgs args) =>
 		{
 			int num2 = 0;
 			ItemDrop[] array = UnityEngine.Object.FindObjectsOfType<ItemDrop>();
@@ -1029,7 +1029,7 @@
 			}
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, "Removed item drops: " + num2);
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("removefish", "remove all fish", delegate
+		new ConsoleCommand("removefish", "remove all fish", (ConsoleEventArgs args) =>
 		{
 			int num2 = 0;
 			Fish[] array = UnityEngine.Object.FindObjectsOfType<Fish>();
@@ -1044,7 +1044,7 @@
 			}
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, "Removed fish: " + num2);
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("printcreatures", "shows counts and levels of active creatures", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("printcreatures", "shows counts and levels of active creatures", (ConsoleEventArgs args) =>
 		{
 			Dictionary<string, Dictionary<int, int>> counts = new Dictionary<string, Dictionary<int, int>>();
 			GetInfo(Character.GetAllCharacters());
@@ -1088,8 +1088,23 @@
 					}
 				}
 			}
+			void count(string key, int level, int increment = 1)
+			{
+				if (!counts.TryGetValue(key, out var value))
+				{
+					value = (counts[key] = new Dictionary<int, int>());
+				}
+				if (value.TryGetValue(level, out var value2))
+				{
+					value[level] = value2 + increment;
+				}
+				else
+				{
+					value[level] = increment;
+				}
+			}
 		}, isCheat: true);
-		new ConsoleCommand("printnetobj", "[radius = 5] lists number of network objects by name surrounding the player", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("printnetobj", "[radius = 5] lists number of network objects by name surrounding the player", (ConsoleEventArgs args) =>
 		{
 			float num2 = args.TryParameterFloat(1, 5f);
 			ZNetView[] array = UnityEngine.Object.FindObjectsOfType<ZNetView>();
@@ -1131,7 +1146,7 @@
 				}
 			}
 		}, isCheat: true);
-		new ConsoleCommand("removebirds", "remove all birds", delegate
+		new ConsoleCommand("removebirds", "remove all birds", (ConsoleEventArgs args) =>
 		{
 			int num2 = 0;
 			RandomFlyingBird[] array = UnityEngine.Object.FindObjectsOfType<RandomFlyingBird>();
@@ -1146,7 +1161,7 @@
 			}
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, "Removed birds: " + num2);
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("printlocations", "shows counts of loaded locations", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("printlocations", "shows counts of loaded locations", (ConsoleEventArgs args) =>
 		{
 			new Dictionary<string, Dictionary<int, int>>();
 			Location[] array = UnityEngine.Object.FindObjectsOfType<Location>();
@@ -1155,7 +1170,7 @@
 				args.Context.AddString(string.Format("   {0}, Dist: {1}, Offset: {2}", location.name, Vector3.Distance(Player.m_localPlayer.transform.position, location.transform.position).ToString("0.0"), location.transform.position - Player.m_localPlayer.transform.position));
 			}
 		}, isCheat: true);
-		new ConsoleCommand("find", "[text] [pingmax] searches loaded objects and location list matching name and pings them on the map. pingmax defaults to 1, if more will place pins on map instead", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("find", "[text] [pingmax] searches loaded objects and location list matching name and pings them on the map. pingmax defaults to 1, if more will place pins on map instead", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -1166,7 +1181,9 @@
 			list.Sort((Tuple<object, Vector3> a, Tuple<object, Vector3> b) => Vector3.Distance(a.Item2, Player.m_localPlayer.transform.position).CompareTo(Vector3.Distance(b.Item2, Player.m_localPlayer.transform.position)));
 			foreach (Tuple<object, Vector3> item11 in list)
 			{
-				args.Context.AddString(string.Format("   {0}, Dist: {1}, Pos: {2}", (item11.Item1 is GameObject gameObject) ? gameObject.name.ToString() : ((item11.Item1 is ZoneSystem.LocationInstance locationInstance) ? locationInstance.m_location.m_prefab.Name : "unknown"), Vector3.Distance(Player.m_localPlayer.transform.position, item11.Item2).ToString("0.0"), item11.Item2));
+				Terminal context = args.Context;
+				string arg = ((item11.Item1 is GameObject gameObject) ? gameObject.name.ToString() : ((item11.Item1 is ZoneSystem.LocationInstance locationInstance) ? locationInstance.m_location.m_prefab.Name : "unknown"));
+				context.AddString(string.Format("   {0}, Dist: {1}, Pos: {2}", arg, Vector3.Distance(Player.m_localPlayer.transform.position, item11.Item2).ToString("0.0"), item11.Item2));
 			}
 			foreach (Minimap.PinData findPin in args.Context.m_findPins)
 			{
@@ -1188,7 +1205,7 @@
 			args.Context.AddString($"Found {list.Count} objects containing '{text}'");
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, findOpt);
-		new ConsoleCommand("findtp", "[text] [index=-1] [closerange=30] searches loaded objects and location list matching name and teleports you to the closest one outside of closerange. Specify an index to tp to any other in the found list, a minus value means index by closest.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("findtp", "[text] [index=-1] [closerange=30] searches loaded objects and location list matching name and teleports you to the closest one outside of closerange. Specify an index to tp to any other in the found list, a minus value means index by closest.", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2 || Player.m_localPlayer == null)
 			{
@@ -1223,7 +1240,7 @@
 			args.Context.AddString($"Found {list.Count} objects containing '{text}'");
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, findOpt);
-		new ConsoleCommand("setfuel", "[amount=10] Sets all light fuel to specified amount", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("setfuel", "[amount=10] Sets all light fuel to specified amount", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer == null)
 			{
@@ -1238,12 +1255,12 @@
 			}
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("freefly", "freefly photo mode", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("freefly", "freefly photo mode", (ConsoleEventArgs args) =>
 		{
 			args.Context.AddString("Toggling free fly camera");
 			GameCamera.instance.ToggleFreeFly();
 		});
-		new ConsoleCommand("ffsmooth", "freefly smoothness", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("ffsmooth", "freefly smoothness", (ConsoleEventArgs args) =>
 		{
 			if (args.Length <= 1)
 			{
@@ -1258,7 +1275,7 @@
 			}
 			return false;
 		});
-		new ConsoleCommand("location", "[SAVE*] spawn location (CAUTION: saving permanently disabled, *unless you specify SAVE)", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("location", "[SAVE*] spawn location (CAUTION: saving permanently disabled, *unless you specify SAVE)", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -1268,7 +1285,7 @@
 			Vector3 pos = Player.m_localPlayer.transform.position + Player.m_localPlayer.transform.forward * 10f;
 			ZoneSystem.instance.TestSpawnLocation(text, pos, args.Length < 3 || args[2] != "SAVE");
 			return true;
-		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			if (Game.instance == null)
@@ -1284,13 +1301,13 @@
 			}
 			return list;
 		}, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("haslocation", "check if zone has location", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("haslocation", "check if zone has location", (ConsoleEventArgs args) =>
 		{
 			Vector3 position = Player.m_localPlayer.transform.position;
 			bool flag = ZoneSystem.instance.ZoneHasLocation(position);
 			args.Context.AddString($"Location in zone [{ZoneSystem.GetZone(position)}]: " + (flag ? "YES" : "NO"));
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("vegetation", "spawn vegetation", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("vegetation", "spawn vegetation", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -1327,19 +1344,19 @@
 					{
 						identity = Quaternion.Euler(x, y, z);
 					}
-					GameObject obj = UnityEngine.Object.Instantiate(item12.m_prefab, p, identity);
-					obj.GetComponent<ZNetView>().SetLocalScale(new Vector3(num2, num2, num2));
-					Collider[] componentsInChildren = obj.GetComponentsInChildren<Collider>();
-					foreach (Collider obj2 in componentsInChildren)
-					{
-						obj2.enabled = false;
-						obj2.enabled = true;
+					GameObject gameObject = UnityEngine.Object.Instantiate(item12.m_prefab, p, identity);
+					gameObject.GetComponent<ZNetView>().SetLocalScale(new Vector3(num2, num2, num2));
+					Collider[] componentsInChildren = gameObject.GetComponentsInChildren<Collider>();
+					foreach (Collider obj in componentsInChildren)
+					{
+						obj.enabled = false;
+						obj.enabled = true;
 					}
 					return true;
 				}
 			}
 			return "No vegeration prefab named '" + args[1] + "' found";
-		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			foreach (ZoneSystem.ZoneVegetation item13 in ZoneSystem.instance.m_vegetation)
@@ -1351,7 +1368,7 @@
 			}
 			return list;
 		}, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("nextseed", "forces the next dungeon to a seed (CAUTION: saving permanently disabled)", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("nextseed", "forces the next dungeon to a seed (CAUTION: saving permanently disabled)", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -1365,14 +1382,14 @@
 			}
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("spawn", "[amount] [level] [radius] [p/e/i] - spawn something. (End word with a star (*) to create each object containing that word.) Add a 'p' after to try to pick up the spawned items, adding 'e' will try to use/equip, 'i' will only spawn and pickup if you don't have one in your inventory.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("spawn", "[amount] [level] [radius] [p/e/i] - spawn something. (End word with a star (*) to create each object containing that word.) Add a 'p' after to try to pick up the spawned items, adding 'e' will try to use/equip, 'i' will only spawn and pickup if you don't have one in your inventory.", (ConsoleEventArgs args) =>
 		{
 			if (args.Length <= 1 || !ZNetScene.instance)
 			{
 				return false;
 			}
 			string text = args[1];
-			int count2 = args.TryParameterInt(2);
+			int count = args.TryParameterInt(2);
 			int level = args.TryParameterInt(3);
 			float radius = args.TryParameterFloat(4, 0.5f);
 			args.TryParameterInt(5, -1);
@@ -1439,7 +1456,7 @@
 				spawn(text);
 			}
 			ZLog.Log("Spawn time :" + (DateTime.Now - now).TotalMilliseconds + " ms");
-			Gogan.LogEvent("Cheat", "Spawn", text, count2);
+			Gogan.LogEvent("Cheat", "Spawn", text, count);
 			return true;
 			void spawn(string name)
 			{
@@ -1450,10 +1467,10 @@
 				}
 				else
 				{
-					Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, "Spawning object " + name + ((count2 == 1) ? "" : $" x{count2}"));
-					for (int j = 0; j < count2; j++)
-					{
-						Vector3 vector = UnityEngine.Random.insideUnitSphere * ((count2 == 1) ? 0f : radius);
+					Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, "Spawning object " + name + ((count == 1) ? "" : $" x{count}"));
+					for (int j = 0; j < count; j++)
+					{
+						Vector3 vector = UnityEngine.Random.insideUnitSphere * ((count == 1) ? 0f : radius);
 						GameObject gameObject = UnityEngine.Object.Instantiate(prefab, Player.m_localPlayer.transform.position + Player.m_localPlayer.transform.forward * 2f + Vector3.up + vector, Quaternion.identity);
 						ZNetView component = gameObject.GetComponent<ZNetView>();
 						if ((object)component != null && component.IsValid())
@@ -1537,7 +1554,7 @@
 				}
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => (!ZNetScene.instance) ? new List<string>() : ZNetScene.instance.GetPrefabNames(), alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("catch", "[fishname] [level] simulates catching a fish", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("catch", "[fishname] [level] simulates catching a fish", (ConsoleEventArgs args) =>
 		{
 			string text = args[1];
 			int a = args.TryParameterInt(2);
@@ -1552,9 +1569,9 @@
 			{
 				return "No fish prefab named: " + text;
 			}
-			GameObject obj = UnityEngine.Object.Instantiate(prefab, Player.m_localPlayer.transform.position, Quaternion.identity);
-			componentInChildren = obj.GetComponentInChildren<Fish>();
-			ItemDrop component = obj.GetComponent<ItemDrop>();
+			GameObject gameObject = UnityEngine.Object.Instantiate(prefab, Player.m_localPlayer.transform.position, Quaternion.identity);
+			componentInChildren = gameObject.GetComponentInChildren<Fish>();
+			ItemDrop component = gameObject.GetComponent<ItemDrop>();
 			if ((bool)component)
 			{
 				component.SetQuality(a);
@@ -1567,7 +1584,7 @@
 			"Fish1", "Fish2", "Fish3", "Fish4_cave", "Fish5", "Fish6", "Fish7", "Fish8", "Fish9", "Fish10",
 			"Fish11", "Fish12"
 		});
-		new ConsoleCommand("itemset", "[name] [item level override] [keep] - spawn a premade named set, add 'keep' to not drop current items.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("itemset", "[name] [item level override] [keep] - spawn a premade named set, add 'keep' to not drop current items.", (ConsoleEventArgs args) =>
 		{
 			if (args.Length >= 2)
 			{
@@ -1576,7 +1593,7 @@
 			}
 			return "Specify name of itemset.";
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () => ItemSets.instance.GetSetNames(), alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("pos", "print current player position", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("pos", "print current player position", (ConsoleEventArgs args) =>
 		{
 			Player localPlayer = Player.m_localPlayer;
 			if ((bool)localPlayer && (bool)ZoneSystem.instance)
@@ -1584,7 +1601,7 @@
 				args.Context?.AddString(string.Format("Player position (X,Y,Z): {0} , Zone: {1}, Center dist: {2}", localPlayer.transform.position.ToString("F0"), ZoneSystem.GetZone(localPlayer.transform.position), Utils.DistanceXZ(Vector3.zero, localPlayer.transform.position)));
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("recall", "[*name] recalls players to you, optionally that match given name", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("recall", "[*name] recalls players to you, optionally that match given name", (ConsoleEventArgs args) =>
 		{
 			foreach (ZNetPeer peer in ZNet.instance.GetPeers())
 			{
@@ -1594,7 +1611,7 @@
 				}
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("goto", "[x,z] - teleport", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("goto", "[x,z] - teleport", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 3 || !args.TryParameterInt(1, out var value) || !args.TryParameterInt(2, out var value2))
 			{
@@ -1611,19 +1628,19 @@
 			Gogan.LogEvent("Cheat", "Goto", "", 0L);
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("exploremap", "explore entire map", delegate
+		new ConsoleCommand("exploremap", "explore entire map", (ConsoleEventArgs args) =>
 		{
 			Minimap.instance.ExploreAll();
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("resetmap", "reset map exploration", delegate
+		new ConsoleCommand("resetmap", "reset map exploration", (ConsoleEventArgs args) =>
 		{
 			Minimap.instance.Reset();
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("resetsharedmap", "removes any shared map data from cartography table", delegate
+		new ConsoleCommand("resetsharedmap", "removes any shared map data from cartography table", (ConsoleEventArgs args) =>
 		{
 			Minimap.instance.ResetSharedMapData();
 		});
-		new ConsoleCommand("restartparty", "restart playfab party network", delegate
+		new ConsoleCommand("restartparty", "restart playfab party network", (ConsoleEventArgs args) =>
 		{
 			if (ZNet.m_onlineBackend == OnlineBackendType.PlayFab)
 			{
@@ -1637,22 +1654,22 @@
 				}
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: true);
-		new ConsoleCommand("puke", "empties your stomach of food", delegate
+		new ConsoleCommand("puke", "empties your stomach of food", (ConsoleEventArgs args) =>
 		{
 			if ((bool)Player.m_localPlayer)
 			{
 				Player.m_localPlayer.ClearFood();
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("tame", "tame all nearby tameable creatures", delegate
+		new ConsoleCommand("tame", "tame all nearby tameable creatures", (ConsoleEventArgs args) =>
 		{
 			Tameable.TameAllInArea(Player.m_localPlayer.transform.position, 20f);
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("aggravate", "aggravated all nearby neutrals", delegate
+		new ConsoleCommand("aggravate", "aggravated all nearby neutrals", (ConsoleEventArgs args) =>
 		{
 			BaseAI.AggravateAllInArea(Player.m_localPlayer.transform.position, 20f, BaseAI.AggravatedReason.Damage);
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("killall", "kill nearby creatures", delegate
+		new ConsoleCommand("killall", "kill nearby creatures", (ConsoleEventArgs args) =>
 		{
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
@@ -1677,7 +1694,7 @@
 			}
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, string.Format("Killed {0} monsters{1}", num2, (num3 > 0) ? $" & {num3} spawners." : "."));
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("killenemycreatures", "kill nearby enemies", delegate
+		new ConsoleCommand("killenemycreatures", "kill nearby enemies", (ConsoleEventArgs args) =>
 		{
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
@@ -1691,7 +1708,7 @@
 			}
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, $"Killed {num2} monsters.");
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("killenemies", "kill nearby enemies", delegate
+		new ConsoleCommand("killenemies", "kill nearby enemies", (ConsoleEventArgs args) =>
 		{
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
@@ -1716,7 +1733,7 @@
 			}
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, string.Format("Killed {0} monsters{1}", num2, (num3 > 0) ? $" & {num3} spawners." : "."));
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("killtame", "kill nearby tame creatures.", delegate
+		new ConsoleCommand("killtame", "kill nearby tame creatures.", (ConsoleEventArgs args) =>
 		{
 			List<Character> allCharacters = Character.GetAllCharacters();
 			int num2 = 0;
@@ -1736,7 +1753,7 @@
 			}
 			Player.m_localPlayer.Message(MessageHud.MessageType.TopLeft, "Killing all tame creatures:" + num2);
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("heal", "heal to full health & stamina", delegate
+		new ConsoleCommand("heal", "heal to full health & stamina", (ConsoleEventArgs args) =>
 		{
 			if (!(Player.m_localPlayer == null))
 			{
@@ -1745,14 +1762,14 @@
 				Player.m_localPlayer.AddEitr(Player.m_localPlayer.GetMaxEitr());
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("adrenaline", "sets adrenaline level", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("adrenaline", "sets adrenaline level", (ConsoleEventArgs args) =>
 		{
 			if (!(Player.m_localPlayer == null))
 			{
 				Player.m_localPlayer.AddAdrenaline(args.TryParameterFloat(1, 100f) - Player.m_localPlayer.GetAdrenaline());
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("god", "invincible mode", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("god", "invincible mode", (ConsoleEventArgs args) =>
 		{
 			if (!(Player.m_localPlayer == null))
 			{
@@ -1761,7 +1778,7 @@
 				Gogan.LogEvent("Cheat", "God", Player.m_localPlayer.InGodMode().ToString(), 0L);
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("ghost", "", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("ghost", "", (ConsoleEventArgs args) =>
 		{
 			if (!(Player.m_localPlayer == null))
 			{
@@ -1770,12 +1787,12 @@
 				Gogan.LogEvent("Cheat", "Ghost", Player.m_localPlayer.InGhostMode().ToString(), 0L);
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("nospawn", "toggles natural spawning of monsters", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("nospawn", "toggles natural spawning of monsters", (ConsoleEventArgs args) =>
 		{
 			SpawnSystem.m_nospawn = args.HasArgumentAnywhere("on") || (!args.HasArgumentAnywhere("off") && !SpawnSystem.m_nospawn);
 			args.Context.AddString("Nospawn: " + SpawnSystem.m_nospawn);
 		}, isCheat: true);
-		new ConsoleCommand("beard", "change beard", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("beard", "change beard", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -1786,7 +1803,7 @@
 				Player.m_localPlayer.SetBeard(args[1]);
 			}
 			return true;
-		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, delegate
+		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, () =>
 		{
 			List<string> list = new List<string>();
 			foreach (ItemDrop allItem in ObjectDB.instance.GetAllItems(ItemDrop.ItemData.ItemType.Customization, "Beard"))
@@ -1795,7 +1812,7 @@
 			}
 			return list;
 		});
-		new ConsoleCommand("hair", "change hair", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("hair", "change hair", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -1806,7 +1823,7 @@
 				Player.m_localPlayer.SetHair(args[1]);
 			}
 			return true;
-		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, delegate
+		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true, () =>
 		{
 			List<string> list = new List<string>();
 			foreach (ItemDrop allItem2 in ObjectDB.instance.GetAllItems(ItemDrop.ItemData.ItemType.Customization, "Hair"))
@@ -1815,7 +1832,7 @@
 			}
 			return list;
 		});
-		new ConsoleCommand("model", "change player model", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("model", "change player model", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -1827,7 +1844,7 @@
 			}
 			return true;
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: true);
-		new ConsoleCommand("tod", "-1 OR [0-1]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("tod", "-1 OR [0-1]", (ConsoleEventArgs args) =>
 		{
 			if (EnvMan.instance == null || args.Length < 2 || !args.TryParameterFloat(1, out var value))
 			{
@@ -1845,7 +1862,7 @@
 			}
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("env", "[env] override environment", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("env", "[env] override environment", (ConsoleEventArgs args) =>
 		{
 			if (EnvMan.instance == null)
 			{
@@ -1862,7 +1879,7 @@
 			args.Context.AddString("Setting debug enviornment:" + text);
 			EnvMan.instance.m_debugEnv = text;
 			return true;
-		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			foreach (EnvSetup environment in EnvMan.instance.m_environments)
@@ -1871,7 +1888,7 @@
 			}
 			return list;
 		});
-		new ConsoleCommand("snow", "[amount] adds/removes amount of snowbuild on all nearby buildpieces", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("snow", "[amount] adds/removes amount of snowbuild on all nearby buildpieces", (ConsoleEventArgs args) =>
 		{
 			if (EnvMan.instance == null)
 			{
@@ -1891,7 +1908,7 @@
 			}
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("updatecover", "force update cover refresh", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("updatecover", "force update cover refresh", (ConsoleEventArgs args) =>
 		{
 			if (EnvMan.instance == null)
 			{
@@ -1907,7 +1924,7 @@
 			}
 			return true;
 		}, isCheat: false, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: true);
-		new ConsoleCommand("resetenv", "disables environment override", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetenv", "disables environment override", (ConsoleEventArgs args) =>
 		{
 			if (EnvMan.instance == null)
 			{
@@ -1917,7 +1934,7 @@
 			EnvMan.instance.m_debugEnv = "";
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("cinematic", "[name] play cinematic", (ConsoleEventArgs args) => (EnvMan.instance == null || args.Length < 2) ? ((object)false) : ((object)CinematicsManager.Play(string.Join(" ", args.Args, 1, args.Args.Length - 1))), isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, delegate
+		new ConsoleCommand("cinematic", "[name] play cinematic", (ConsoleEventArgs args) => (EnvMan.instance == null || args.Length < 2) ? ((object)false) : ((object)CinematicsManager.Play(string.Join(" ", args.Args, 1, args.Args.Length - 1))), isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			foreach (CinematicsManager.VideoEntry video in CinematicsManager.s_instance.m_videos)
@@ -1926,7 +1943,7 @@
 			}
 			return list;
 		});
-		new ConsoleCommand("unlockcinematics", "toggles unlocking all cinematics in the main menu", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("unlockcinematics", "toggles unlocking all cinematics in the main menu", (ConsoleEventArgs args) =>
 		{
 			if (FejdStartup.instance != null && FejdStartup.instance.m_cinematicsInitialized)
 			{
@@ -1938,7 +1955,7 @@
 				args.Context.AddString($"All cinematics unlocked : {CinematicsManager.m_allUnlocked}");
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("inventorysize", "sets inventory size", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("inventorysize", "sets inventory size", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer == null)
 			{
@@ -1951,7 +1968,7 @@
 			}
 			return $"Inventory size: {Player.m_localPlayer.GetInventory().GetHeight()}";
 		}, isCheat: true, isNetwork: false, onlyServer: true, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("cinematicsleep", "[name] play cinematic on next sleep for everyone", (ConsoleEventArgs args) => (EnvMan.instance == null || args.Length < 2) ? ((object)false) : ((object)CinematicsManager.SetDreamCinematic(string.Join(" ", args.Args, 1, args.Args.Length - 1))), isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, delegate
+		new ConsoleCommand("cinematicsleep", "[name] play cinematic on next sleep for everyone", (ConsoleEventArgs args) => (EnvMan.instance == null || args.Length < 2) ? ((object)false) : ((object)CinematicsManager.SetDreamCinematic(string.Join(" ", args.Args, 1, args.Args.Length - 1))), isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			foreach (CinematicsManager.VideoEntry video2 in CinematicsManager.s_instance.m_videos)
@@ -1960,11 +1977,11 @@
 			}
 			return list;
 		});
-		new ConsoleCommand("inventoryclean", "throws out any items in inventory on invalid positions", delegate
+		new ConsoleCommand("inventoryclean", "throws out any items in inventory on invalid positions", (ConsoleEventArgs args) =>
 		{
 			Player.m_localPlayer.DropInvalidItems();
 		});
-		new ConsoleCommand("wind", "[angle] [intensity]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("wind", "[angle] [intensity]", (ConsoleEventArgs args) =>
 		{
 			if (args.TryParameterFloat(1, out var value) && args.TryParameterFloat(2, out var value2))
 			{
@@ -1973,20 +1990,20 @@
 			}
 			return false;
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("resetwind", "", delegate
+		new ConsoleCommand("resetwind", "", (ConsoleEventArgs args) =>
 		{
 			EnvMan.instance.ResetDebugWind();
 		}, isCheat: true, isNetwork: false, onlyServer: true);
-		new ConsoleCommand("clear", "clear the console window", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("clear", "clear the console window", (ConsoleEventArgs args) =>
 		{
 			args.Context.m_chatBuffer.Clear();
 			args.Context.UpdateChat();
 		});
-		new ConsoleCommand("clearpopups", "stops all current unlock UI messages", delegate
+		new ConsoleCommand("clearpopups", "stops all current unlock UI messages", (ConsoleEventArgs args) =>
 		{
 			MessageHud.instance.ClearUnlockQueue();
 		});
-		new ConsoleCommand("filtercraft", "[name] filters crafting list to contain part of text", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("filtercraft", "[name] filters crafting list to contain part of text", (ConsoleEventArgs args) =>
 		{
 			if (args.Length <= 1)
 			{
@@ -1998,12 +2015,12 @@
 				Player.s_FilterCraft = args.ArgsAll.Split(' ').ToList();
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true);
-		new ConsoleCommand("clearstatus", "clear any status modifiers", delegate
+		new ConsoleCommand("clearstatus", "clear any status modifiers", (ConsoleEventArgs args) =>
 		{
 			Player.m_localPlayer.ClearHardDeath();
 			Player.m_localPlayer.GetSEMan().RemoveAllStatusEffects();
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("addstatus", "[name] adds a status effect (ex: Rested, Burning, SoftDeath, Wet, etc)", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("addstatus", "[name] adds a status effect (ex: Rested, Burning, SoftDeath, Wet, etc)", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2011,7 +2028,7 @@
 			}
 			Player.m_localPlayer.GetSEMan().AddStatusEffect(args[1].GetStableHashCode(), resetTime: true, 0, 0f, -1);
 			return true;
-		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, () =>
 		{
 			List<StatusEffect> statusEffects = ObjectDB.instance.m_StatusEffects;
 			List<string> list = new List<string>();
@@ -2021,7 +2038,7 @@
 			}
 			return list;
 		}, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("setpower", "[name] sets your current guardian power and resets cooldown (ex: GP_Eikthyr, GP_TheElder, etc)", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("setpower", "[name] sets your current guardian power and resets cooldown (ex: GP_Eikthyr, GP_TheElder, etc)", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2030,7 +2047,7 @@
 			Player.m_localPlayer.SetGuardianPower(args[1]);
 			Player.m_localPlayer.m_guardianPowerCooldown = 0f;
 			return true;
-		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true, hideBehindDevCommands: false, () =>
 		{
 			List<StatusEffect> statusEffects = ObjectDB.instance.m_StatusEffects;
 			List<string> list = new List<string>();
@@ -2040,7 +2057,7 @@
 			}
 			return list;
 		}, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("bind", "[keycode] [command and parameters] bind a key to a console command. note: may cause conflicts with game controls", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("bind", "[keycode] [command and parameters] bind a key to a console command. note: may cause conflicts with game controls", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2062,7 +2079,7 @@
 			}
 			return true;
 		});
-		new ConsoleCommand("unbind", "[keycode] clears all binds connected to keycode", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("unbind", "[keycode] clears all binds connected to keycode", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2078,14 +2095,14 @@
 			updateBinds();
 			return true;
 		});
-		new ConsoleCommand("printbinds", "prints current binds", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("printbinds", "prints current binds", (ConsoleEventArgs args) =>
 		{
 			foreach (string bind in m_bindList)
 			{
 				args.Context.AddString(bind);
 			}
 		});
-		new ConsoleCommand("resetbinds", "resets all custom binds to default dev commands", delegate
+		new ConsoleCommand("resetbinds", "resets all custom binds to default dev commands", (ConsoleEventArgs args) =>
 		{
 			for (int num2 = m_bindList.Count - 1; num2 >= 0; num2--)
 			{
@@ -2093,14 +2110,14 @@
 			}
 			updateBinds();
 		});
-		new ConsoleCommand("height", "prints height from worldgen at current position", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("height", "prints height from worldgen at current position", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayerExists)
 			{
 				args.Context.AddString($"{WorldGenerator.instance.GetHeight(Player.m_localPlayer.transform.position)}");
 			}
 		});
-		new ConsoleCommand("pevents", "Subcommands: [list/start/stop/here]", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("pevents", "Subcommands: [list/start/stop/here]", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2166,18 +2183,18 @@
 				}
 			}
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("tombstone", "[name] creates a tombstone with given name", delegate(ConsoleEventArgs args)
-		{
-			GameObject obj = UnityEngine.Object.Instantiate(Player.m_localPlayer.m_tombstone, Player.m_localPlayer.GetCenterPoint(), Player.m_localPlayer.transform.rotation);
-			Container component = obj.GetComponent<Container>();
+		new ConsoleCommand("tombstone", "[name] creates a tombstone with given name", (ConsoleEventArgs args) =>
+		{
+			GameObject gameObject = UnityEngine.Object.Instantiate(Player.m_localPlayer.m_tombstone, Player.m_localPlayer.GetCenterPoint(), Player.m_localPlayer.transform.rotation);
+			Container component = gameObject.GetComponent<Container>();
 			ItemDrop coinPrefab = StoreGui.instance.m_coinPrefab;
 			component.GetInventory().AddItem(coinPrefab.gameObject.name, 1, coinPrefab.m_itemData.m_quality, coinPrefab.m_itemData.m_variant, 0L, "", cheated: true, pickedUp: true);
-			TombStone component2 = obj.GetComponent<TombStone>();
+			TombStone component2 = gameObject.GetComponent<TombStone>();
 			PlayerProfile playerProfile = Game.instance.GetPlayerProfile();
 			string ownerName = ((args.Args.Length >= 2) ? args.Args[1] : playerProfile.GetName());
 			component2.Setup(ownerName, playerProfile.GetPlayerID());
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("test", "[key] [value] set test string, with optional value. set empty existing key to remove", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("test", "[key] [value] set test string, with optional value. set empty existing key to remove", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2215,7 +2232,7 @@
 			}
 			return true;
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: true);
-		new ConsoleCommand("forcedelete", "[radius] [*name] force remove all objects within given radius. If name is entered, only deletes items with matching names. Caution! Use at your own risk. Make backups! Radius default: 5, max: 150.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("forcedelete", "[radius] [*name] force remove all objects within given radius. If name is entered, only deletes items with matching names. Caution! Use at your own risk. Make backups! Radius default: 5, max: 150.", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer == null)
 			{
@@ -2246,7 +2263,7 @@
 			}
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("stopfire", "Puts out all spreading fires and smoke", delegate
+		new ConsoleCommand("stopfire", "Puts out all spreading fires and smoke", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer == null)
 			{
@@ -2256,7 +2273,7 @@
 			RemoveObj(UnityEngine.Object.FindObjectsOfType(typeof(Smoke)));
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("stopsmoke", "Puts out all spreading fires", delegate
+		new ConsoleCommand("stopsmoke", "Puts out all spreading fires", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer == null)
 			{
@@ -2279,7 +2296,7 @@
 			}
 			return true;
 		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("repairall", "repairs all equipment", delegate
+		new ConsoleCommand("repairall", "repairs all equipment", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer == null)
 			{
@@ -2293,7 +2310,7 @@
 			}
 			return true;
 		}, isCheat: true);
-		new ConsoleCommand("printseeds", "print seeds of loaded dungeons", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("printseeds", "print seeds of loaded dungeons", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer == null)
 			{
@@ -2310,7 +2327,7 @@
 			}
 			return true;
 		});
-		new ConsoleCommand("nomap", "disables map for this character. If used as host, will disable for all joining players from now on.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("nomap", "disables map for this character. If used as host, will disable for all joining players from now on.", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer != null)
 			{
@@ -2332,7 +2349,7 @@
 				}
 			}
 		});
-		new ConsoleCommand("noportals", "disables portals for server.", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("noportals", "disables portals for server.", (ConsoleEventArgs args) =>
 		{
 			if (Player.m_localPlayer != null)
 			{
@@ -2348,7 +2365,7 @@
 				args.Context?.AddString("Portals " + (globalKey ? "enabled" : "disabled"));
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
-		new ConsoleCommand("resetspawn", "resets spawn location", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetspawn", "resets spawn location", (ConsoleEventArgs args) =>
 		{
 			if (!Game.instance)
 			{
@@ -2358,7 +2375,7 @@
 			args.Context?.AddString("Reseting spawn point");
 			return true;
 		});
-		new ConsoleCommand("respawntime", "sets respawntime", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("respawntime", "sets respawntime", (ConsoleEventArgs args) =>
 		{
 			if (!Game.instance)
 			{
@@ -2370,7 +2387,7 @@
 			}
 			return true;
 		}, isCheat: true);
-		new ConsoleCommand("die", "kill yourself", delegate
+		new ConsoleCommand("die", "kill yourself", (ConsoleEventArgs args) =>
 		{
 			if (!Player.m_localPlayer)
 			{
@@ -2387,7 +2404,7 @@
 			Player.m_localPlayer.Damage(hit);
 			return true;
 		});
-		new ConsoleCommand("say", "chat message", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("say", "chat message", (ConsoleEventArgs args) =>
 		{
 			if (args.FullLine.Length < 5 || Chat.instance == null)
 			{
@@ -2396,7 +2413,7 @@
 			Chat.instance.SendText(Talker.Type.Normal, args.FullLine.Substring(4));
 			return true;
 		});
-		new ConsoleCommand("s", "shout message", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("s", "shout message", (ConsoleEventArgs args) =>
 		{
 			if (args.FullLine.Length < 3 || Chat.instance == null)
 			{
@@ -2405,7 +2422,7 @@
 			Chat.instance.SendText(Talker.Type.Shout, args.FullLine.Substring(2));
 			return true;
 		});
-		new ConsoleCommand("w", "[playername] whispers a private message to a player", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("w", "[playername] whispers a private message to a player", (ConsoleEventArgs args) =>
 		{
 			if (args.FullLine.Length < 3 || Chat.instance == null)
 			{
@@ -2414,7 +2431,7 @@
 			Chat.instance.SendText(Talker.Type.Whisper, args.FullLine.Substring(2));
 			return true;
 		});
-		new ConsoleCommand("resetplayerprefs", "Resets any saved settings and variables (not the save game)", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetplayerprefs", "Resets any saved settings and variables (not the save game)", (ConsoleEventArgs args) =>
 		{
 			PlatformPrefs.DeleteAll();
 			args.Context?.AddString("Reset saved player preferences");
@@ -2422,12 +2439,12 @@
 		for (int num = 0; num < 25; num++)
 		{
 			Emotes emote = (Emotes)num;
-			new ConsoleCommand(emote.GetCommandName(), $"emote: {emote}", delegate
+			new ConsoleCommand(emote.GetCommandName(), $"emote: {emote}", (ConsoleEventArgs args) =>
 			{
 				Emote.DoEmote(emote);
 			});
 		}
-		new ConsoleCommand("resetbuildui", "Resets build ui save data that stores recent and favorites", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("resetbuildui", "Resets build ui save data that stores recent and favorites", (ConsoleEventArgs args) =>
 		{
 			if ((bool)Hud.instance)
 			{
@@ -2439,12 +2456,12 @@
 				args.Context?.AddString("The build UI can only be reset after having entered a world");
 			}
 		}, isCheat: false, isNetwork: false, onlyServer: false, isSecret: true, allowInDevBuild: true);
-		new ConsoleCommand("biomeinfo", "info about current biome sector", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("biomeinfo", "info about current biome sector", (ConsoleEventArgs args) =>
 		{
 			BiomeSector biomeSector = WorldGenerator.instance.GetBiomeSector(Player.m_localPlayer.transform.position);
 			args.Context.AddString(biomeSector.ToString());
 		}, isCheat: true);
-		new ConsoleCommand("altbioms", "list of biomes with modifiers", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("altbioms", "list of biomes with modifiers", (ConsoleEventArgs args) =>
 		{
 			Dictionary<Heightmap.Biome, int> dictionary = new Dictionary<Heightmap.Biome, int>();
 			AltBiomeWorldData biomeData = WorldGenerator.instance.m_world.m_biomeData;
@@ -2489,7 +2506,7 @@
 				}
 			}
 		}, isCheat: true);
-		new ConsoleCommand("findbiome", "marks center of all biomes on map of type or containing modifier with search string", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("findbiome", "marks center of all biomes on map of type or containing modifier with search string", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2534,7 +2551,7 @@
 			}
 			args.Context.AddString($"Found {list.Count} biomes containing '{text}'");
 			return true;
-		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			list.AddRange(Enum.GetNames(typeof(Heightmap.Biome)));
@@ -2559,7 +2576,7 @@
 			}
 			return list;
 		});
-		new ConsoleCommand("findbiometp", "finds the closest biome matching your search and teleports you to it", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("findbiometp", "finds the closest biome matching your search and teleports you to it", (ConsoleEventArgs args) =>
 		{
 			if (args.Length < 2)
 			{
@@ -2594,7 +2611,7 @@
 				Player.m_localPlayer.TeleportTo(new Vector3(list[0].Center.x, 0f, list[0].Center.y), Player.m_localPlayer.transform.rotation, distantTeleport: true);
 			}
 			return true;
-		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, delegate
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, () =>
 		{
 			List<string> list = new List<string>();
 			list.AddRange(Enum.GetNames(typeof(Heightmap.Biome)));
@@ -2635,21 +2652,6 @@
 				return false;
 			}
 			return true;
-		}
-		void count(string key, int level, int increment = 1)
-		{
-			if (!P_3.counts.TryGetValue(key, out var value))
-			{
-				value = (P_3.counts[key] = new Dictionary<int, int>());
-			}
-			if (value.TryGetValue(level, out var value2))
-			{
-				value[level] = value2 + increment;
-			}
-			else
-			{
-				value[level] = increment;
-			}
 		}
 		static List<Tuple<object, Vector3>> find(string q)
 		{
@@ -2724,7 +2726,7 @@
 
 	private static void AddConsoleCheatCommands()
 	{
-		new ConsoleCommand("xb:version", "Prints mercurial hashset used for this build", delegate(ConsoleEventArgs args)
+		new ConsoleCommand("xb:version", "Prints mercurial hashset used for this build", (ConsoleEventArgs args) =>
 		{
 			args.Context?.AddString("Buildhash: " + Version.GetVersionString(includeMercurialHash: true));
 		});
@@ -2943,7 +2945,15 @@
 			updateSearch(array2[0], m_commandList, usePrefix: true);
 			return;
 		}
-		string key2 = ((m_tabPrefix == '\0') ? array2[0] : ((array2[0].Length == 0) ? "" : array2[0].Substring(1)));
+		string key2;
+		if (m_tabPrefix != 0)
+		{
+			key2 = ((array2[0].Length == 0) ? "" : array2[0].Substring(1));
+		}
+		else
+		{
+			key2 = array2[0];
+		}
 		if (commands.TryGetValue(key2, out var value2))
 		{
 			updateSearch(array2[1], value2.GetTabOptions(), usePrefix: false);
```
