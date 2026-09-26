# `ZNet.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+26/-25` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZNet.cs
+++ b/ZNet.cs
@@ -482,7 +482,7 @@
 			if (m_serverSteamID == 0L)
 			{
 				ZLog.Log("Connecting to server with Steam-backend " + m_serverHost + ":" + m_serverHostPort);
-				SteamNetworkingIPAddr host = default(SteamNetworkingIPAddr);
+				SteamNetworkingIPAddr host = default;
 				host.ParseString(m_serverHost + ":" + m_serverHostPort);
 				Connect(host);
 				return;
@@ -599,9 +599,9 @@
 			{
 				m_httpClient.Timeout = TimeSpan.FromMilliseconds(timeoutMS);
 				m_httpClient.GetAsync(downloadUrl);
-				HttpResponseMessage obj = await m_httpClient.GetAsync(downloadUrl);
-				obj.EnsureSuccessStatusCode();
-				return await obj.Content.ReadAsStringAsync();
+				HttpResponseMessage httpResponseMessage = await m_httpClient.GetAsync(downloadUrl);
+				httpResponseMessage.EnsureSuccessStatusCode();
+				return await httpResponseMessage.Content.ReadAsStringAsync();
 			}
 			catch (Exception ex2)
 			{
@@ -649,14 +649,14 @@
 			Save(sync: true);
 		}
 		StopAll();
-		base.enabled = false;
+		enabled = false;
 	}
 
 	public void ShutdownWithoutSave(bool suspending)
 	{
 		ZLog.Log("ZNet Shutdown without save");
 		StopAll(suspending);
-		base.enabled = false;
+		enabled = false;
 	}
 
 	private void StopAll(bool suspending = false)
@@ -964,7 +964,7 @@
 			pkg.Write(data);
 			pkg.Write(m_inviteSecretKey);
 			rpc.GetSocket().GetHostName();
-			SteamNetworkingIdentity serverIdentity = default(SteamNetworkingIdentity);
+			SteamNetworkingIdentity serverIdentity = default;
 			serverIdentity.SetSteamID(new CSteamID(m_serverSteamID));
 			byte[] array = ZSteamMatchmaking.instance.RequestSessionTicket(ref serverIdentity);
 			if (array == null)
@@ -1004,7 +1004,7 @@
 			{
 				m_connectionStatus = ConnectionStatus.ErrorVersion;
 			}
-			string[] obj = new string[11]
+			string[] array = new string[11]
 			{
 				"Peer ",
 				name,
@@ -1019,11 +1019,11 @@
 				null
 			};
 			GameVersion gameVersion = version;
-			obj[7] = gameVersion.ToString();
-			obj[8] = " (network version ";
-			obj[9] = ((num == uint.MaxValue) ? "unknown" : num.ToString());
-			obj[10] = ")";
-			ZLog.Log(string.Concat(obj));
+			array[7] = gameVersion.ToString();
+			array[8] = " (network version ";
+			array[9] = ((num == uint.MaxValue) ? "unknown" : num.ToString());
+			array[10] = ")";
+			ZLog.Log(string.Concat(array));
 			return;
 		}
 		Vector3 refPos = pkg.ReadVector3();
@@ -1075,7 +1075,7 @@
 					ZLog.Log("Peer diconnected due to server platform privileges disallowing crossplay. Server platform: " + PlatformManager.DistributionPlatform.Platform.ToString() + "   Peer platform: " + platformUserID.m_platform.ToString());
 					return;
 				}
-				PlayFabManager.CheckIfUserAuthenticated((peer.m_socket as ZPlayFabSocket).m_remotePlayerId, platformUserID, delegate(bool isAuthenticated)
+				PlayFabManager.CheckIfUserAuthenticated((peer.m_socket as ZPlayFabSocket).m_remotePlayerId, platformUserID, (bool isAuthenticated) =>
 				{
 					if (!isAuthenticated)
 					{
@@ -1348,7 +1348,7 @@
 
 	private void RPC_Save(ZRpc rpc)
 	{
-		if (!base.enabled)
+		if (!enabled)
 		{
 			return;
 		}
@@ -1478,11 +1478,11 @@
 			else if (exitGamePrompt)
 			{
 				string text = "$menu_lowdisk_block_exitanyway_prompt";
-				UnifiedPopup.Push(new YesNoPopup("$menu_lowdisk_block_exitanyway_header", text, delegate
+				UnifiedPopup.Push(new YesNoPopup("$menu_lowdisk_block_exitanyway_header", text, () =>
 				{
 					onDecisionMade?.Invoke(obj: true);
 					UnifiedPopup.Pop();
-				}, delegate
+				}, () =>
 				{
 					onDecisionMade?.Invoke(obj: false);
 					UnifiedPopup.Pop();
@@ -1507,7 +1507,7 @@
 	private void SavingBlockedPopup()
 	{
 		string text = "$menu_lowdisk_message_block";
-		UnifiedPopup.Push(new WarningPopup("$menu_lowdisk_header_block", text, delegate
+		UnifiedPopup.Push(new WarningPopup("$menu_lowdisk_header_block", text, () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -1516,7 +1516,7 @@
 	private void SaveLowDiskWarningPopup()
 	{
 		string text = "$menu_lowdisk_message_warn";
-		UnifiedPopup.Push(new WarningPopup("$menu_lowdisk_header_warn", text, delegate
+		UnifiedPopup.Push(new WarningPopup("$menu_lowdisk_header_warn", text, () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -1918,15 +1918,15 @@
 
 	private bool TryMountAndLogIfFail()
 	{
-		bool num = FileHelpers.Mount(SaveDataAccess.ReadWrite);
-		if (!num)
+		bool flag = FileHelpers.Mount(SaveDataAccess.ReadWrite);
+		if (!flag)
 		{
 			string text = "Error saving world! Failed to mount!";
 			ZLog.LogError(text);
 			Terminal.m_threadSafeMessages.Enqueue("Error saving world! See log or console.");
 			Terminal.m_threadSafeConsoleLog.Enqueue(text);
 		}
-		return num;
+		return flag;
 	}
 
 	public static bool ConsiderAutoBackup(string saveName, SaveDataType dataType, DateTime now)
@@ -2565,7 +2565,8 @@
 		{
 			zPackage.Write(playerInfo.m_name);
 			zPackage.Write(playerInfo.m_characterID);
-			zPackage.Write(playerInfo.m_userInfo.m_id.ToString());
+			PlatformUserID id = playerInfo.m_userInfo.m_id;
+			zPackage.Write(id.ToString());
 			zPackage.Write(playerInfo.m_userInfo.m_displayName);
 			zPackage.Write(playerInfo.m_userInfo.m_serverAssignedDisplayName);
 			zPackage.Write(playerInfo.m_userInfo.m_playfabId);
@@ -2707,7 +2708,7 @@
 	{
 		if (instance == null)
 		{
-			playerInfo = default(PlayerInfo);
+			playerInfo = default;
 			return false;
 		}
 		for (int i = 0; i < instance.m_players.Count; i++)
@@ -2718,7 +2719,7 @@
 				return true;
 			}
 		}
-		playerInfo = default(PlayerInfo);
+		playerInfo = default;
 		return false;
 	}
 
```
