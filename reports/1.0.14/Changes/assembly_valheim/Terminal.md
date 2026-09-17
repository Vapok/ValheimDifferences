# `Terminal.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Terminal.cs
+++ b/Terminal.cs
@@ -1926,6 +1926,18 @@
 			}
 			return list;
 		});
+		new ConsoleCommand("unlockcinematics", "toggles unlocking all cinematics in the main menu", delegate(ConsoleEventArgs args)
+		{
+			if (FejdStartup.instance != null && FejdStartup.instance.m_cinematicsInitialized)
+			{
+				args.Context.AddString("Can't reload unlocked cinematics while in main menu when they've already been loaded once, either enter world, retry command, and log out - or restart game and enter this command before entering the cinematics menu.");
+			}
+			else
+			{
+				CinematicsManager.m_allUnlocked = !CinematicsManager.m_allUnlocked;
+				args.Context.AddString($"All cinematics unlocked : {CinematicsManager.m_allUnlocked}");
+			}
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: true);
 		new ConsoleCommand("inventorysize", "sets inventory size", delegate(ConsoleEventArgs args)
 		{
 			if (Player.m_localPlayer == null)
@@ -2153,7 +2165,7 @@
 					args.Context.AddString($"{item21.eventId}: {item21.internalName} | Position: {item21.position}");
 				}
 			}
-		});
+		}, isCheat: true, isNetwork: false, onlyServer: false, isSecret: false, allowInDevBuild: false, hideBehindDevCommands: false, null, alwaysRefreshTabOptions: false, remoteCommand: false, onlyAdmin: true);
 		new ConsoleCommand("tombstone", "[name] creates a tombstone with given name", delegate(ConsoleEventArgs args)
 		{
 			GameObject obj = UnityEngine.Object.Instantiate(Player.m_localPlayer.m_tombstone, Player.m_localPlayer.GetCenterPoint(), Player.m_localPlayer.transform.rotation);
```
