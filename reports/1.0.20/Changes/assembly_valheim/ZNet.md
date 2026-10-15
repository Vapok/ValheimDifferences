# `ZNet.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZNet.cs
+++ b/ZNet.cs
@@ -409,7 +409,7 @@
 			m_openServer = true;
 			bool flag = m_serverPassword != "";
 			GameVersion currentVersion = Version.CurrentVersion;
-			uint networkVersion = 40u;
+			uint networkVersion = 41u;
 			string[] modifiers = m_world.m_startingGlobalKeys.ToArray();
 			ZSteamMatchmaking.instance.RegisterServer(m_ServerName, flag, currentVersion, modifiers, networkVersion, m_publicServer, m_world.m_seedName, OnSteamServerRegistered);
 			if (m_onlineBackend == OnlineBackendType.Steamworks)
@@ -631,7 +631,7 @@
 			}
 			bool password = m_serverPassword != "";
 			GameVersion currentVersion = Version.CurrentVersion;
-			uint networkVersion = 40u;
+			uint networkVersion = 41u;
 			string[] modifiers = m_world.m_startingGlobalKeys.ToArray();
 			ZSteamMatchmaking.instance.RegisterServer(m_ServerName, password, currentVersion, modifiers, networkVersion, m_publicServer, m_world.m_seedName, OnSteamServerRegistered);
 		}
@@ -944,7 +944,7 @@
 		ZPackage pkg = new ZPackage();
 		pkg.Write(GetUID());
 		pkg.Write(Version.CurrentVersion.ToString());
-		pkg.Write(40u);
+		pkg.Write(41u);
 		pkg.Write(m_referencePosition);
 		pkg.Write(Game.instance.GetPlayerProfile().GetName());
 		pkg.Write(PlayFabManager.instance.PlayFabUniqueId);
@@ -993,8 +993,8 @@
 		}
 		string name = peer.m_socket.GetEndPointString();
 		string hostName = peer.m_socket.GetHostName();
-		ZLog.Log("Network version check, their:" + num + ", mine:" + 40u);
-		if (num != 40)
+		ZLog.Log("Network version check, their:" + num + ", mine:" + 41u);
+		if (num != 41)
 		{
 			if (m_isServer)
 			{
@@ -1011,7 +1011,7 @@
 				" has incompatible version, mine:",
 				Version.CurrentVersion.ToString(),
 				" (network version ",
-				40u.ToString(),
+				41u.ToString(),
 				")   remote ",
 				null,
 				null,
@@ -1837,7 +1837,7 @@
 			stopwatch = Stopwatch.StartNew();
 			FileWriter fileWriter = new FileWriter(text2, CloudStorageFileGrouping.SameFolder, FileHelpers.FileHelperType.Binary, m_world.m_fileSource);
 			BinaryWriter binary = fileWriter.m_binary;
-			binary.Write(41);
+			binary.Write(42);
 			binary.Write(m_netTime);
 			ZoneSystem.instance.Save(binary);
 			RandEventSystem.instance.Save(binary);
@@ -1874,7 +1874,7 @@
 			else
 			{
 				FileWriter fileWriter2 = new FileWriter(path, CloudStorageFileGrouping.SameFolder, FileHelpers.FileHelperType.Binary, m_world.m_fileSource);
-				fileWriter2.m_binary.Write(41);
+				fileWriter2.m_binary.Write(42);
 				fileWriter2.Finish();
 				FileHelpers.Delete(text + SaveSystem.MainFwl2FileName(old: true), m_world.m_fileSource);
 				FileHelpers.Delete(text + SaveSystem.MainDb2FileName(old: true), m_world.m_fileSource);
```
