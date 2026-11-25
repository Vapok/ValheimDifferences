# `ZNet.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnSteamServerRegistered() [Method Body Modified]`
- `OpenServer() [Method Body Modified]`
- `RPC_PeerInfo() [Method Body Modified]`
- `SaveWorldThread() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ZNet.cs
+++ b/ZNet.cs
@@ -409,7 +409,7 @@
 			m_openServer = true;
 			bool flag = m_serverPassword != "";
 			GameVersion currentVersion = Version.CurrentVersion;
-			uint networkVersion = 41u;
+			uint networkVersion = 42u;
 			string[] modifiers = m_world.m_startingGlobalKeys.ToArray();
 			ZSteamMatchmaking.instance.RegisterServer(m_ServerName, flag, currentVersion, modifiers, networkVersion, m_publicServer, m_world.m_seedName, OnSteamServerRegistered);
 			if (m_onlineBackend == OnlineBackendType.Steamworks)
@@ -631,7 +631,7 @@
 			}
 			bool password = m_serverPassword != "";
 			GameVersion currentVersion = Version.CurrentVersion;
-			uint networkVersion = 41u;
+			uint networkVersion = 42u;
 			string[] modifiers = m_world.m_startingGlobalKeys.ToArray();
 			ZSteamMatchmaking.instance.RegisterServer(m_ServerName, password, currentVersion, modifiers, networkVersion, m_publicServer, m_world.m_seedName, OnSteamServerRegistered);
 		}
@@ -944,7 +944,7 @@
 		ZPackage pkg = new ZPackage();
 		pkg.Write(GetUID());
 		pkg.Write(Version.CurrentVersion.ToString());
-		pkg.Write(41u);
+		pkg.Write(42u);
 		pkg.Write(m_referencePosition);
 		pkg.Write(Game.instance.GetPlayerProfile().GetName());
 		pkg.Write(PlayFabManager.instance.PlayFabUniqueId);
@@ -993,8 +993,8 @@
 		}
 		string name = peer.m_socket.GetEndPointString();
 		string hostName = peer.m_socket.GetHostName();
-		ZLog.Log("Network version check, their:" + num + ", mine:" + 41u);
-		if (num != 41)
+		ZLog.Log("Network version check, their:" + num + ", mine:" + 42u);
+		if (num != 42)
 		{
 			if (m_isServer)
 			{
@@ -1011,7 +1011,7 @@
 				" has incompatible version, mine:",
 				Version.CurrentVersion.ToString(),
 				" (network version ",
-				41u.ToString(),
+				42u.ToString(),
 				")   remote ",
 				null,
 				null,
@@ -1815,11 +1815,6 @@
 		{
 			DateTime now2 = DateTime.Now;
 			Stopwatch stopwatch = Stopwatch.StartNew();
-			if (ConsiderAutoBackup(m_world.m_worldName, SaveDataType.World, now))
-			{
-				ZLog.Log("World auto backup saved [" + stopwatch.ElapsedMilliseconds + "ms]");
-			}
-			stopwatch = Stopwatch.StartNew();
 			SaveSystem.PreSaveCloudChecksAndOperations(m_world.m_worldName, SaveDataType.World, ref m_world.m_fileSource, ref m_world.m_createBackupBeforeSaving, ref m_saveExceededCloudQuota, m_zdoMan.NumDirtySaveFiles, m_world);
 			SaveSystem.BeginSave(m_world.m_fileSource);
 			uint saveNumber = SaveSystem.GetSaveNumber();
@@ -1883,6 +1878,11 @@
 				m_zdoMan.DeleteOldChunks(text, m_world.m_fileSource);
 				SaveSystem.EndSave(m_world.m_fileSource, writeOK: true);
 				ZLog.Log("World save (5/5) done. Total time [" + (DateTime.Now - now2).TotalMilliseconds.ToString("N0") + "ms]");
+				stopwatch = Stopwatch.StartNew();
+				if (ConsiderAutoBackup(m_world.m_worldName, SaveDataType.World, now))
+				{
+					ZLog.Log("World auto backup saved [" + stopwatch.ElapsedMilliseconds + "ms]");
+				}
 			}
 		}
 		catch (Exception ex)
```
