# `ZSteamMatchmaking.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-6` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZSteamMatchmaking.cs
+++ b/ZSteamMatchmaking.cs
@@ -134,7 +134,7 @@
 		ReleaseSessionTicket();
 		byte[] array = new byte[1024];
 		uint pcbTicket = 0u;
-		SteamNetworkingIdentity pSteamNetworkingIdentity = default(SteamNetworkingIdentity);
+		SteamNetworkingIdentity pSteamNetworkingIdentity = default;
 		m_authTicket = SteamUser.GetAuthSessionTicket(array, 1024, out pcbTicket, ref pSteamNetworkingIdentity);
 		if (m_authTicket == HAuthTicket.Invalid)
 		{
@@ -343,7 +343,7 @@
 	{
 		ServerPingCompletedHandler completedHandler = m_currentPing.Value.m_completedHandler;
 		m_currentPing = null;
-		m_pingQuery = default(HServerQuery);
+		m_pingQuery = default;
 		completedHandler?.Invoke(serverData);
 	}
 
@@ -375,14 +375,14 @@
 		}
 		if (UnifiedPopup.IsAvailable() && Menu.instance != null)
 		{
-			UnifiedPopup.Push(new YesNoPopup("$menu_joindifferentserver", "$menu_logoutprompt", delegate
+			UnifiedPopup.Push(new YesNoPopup("$menu_joindifferentserver", "$menu_logoutprompt", () =>
 			{
 				UnifiedPopup.Pop();
 				if (Menu.instance != null)
 				{
 					Menu.instance.OnLogoutYes();
 				}
-			}, delegate
+			}, () =>
 			{
 				UnifiedPopup.Pop();
 				m_queuedJoinLobby = CSteamID.Nil;
@@ -801,7 +801,7 @@
 	{
 		if (!m_joinData.IsValid)
 		{
-			joinData = default(ServerJoinData);
+			joinData = default;
 			return false;
 		}
 		joinData = m_joinData;
@@ -813,7 +813,7 @@
 	{
 		gameserveritem_t serverDetails = SteamMatchmakingServers.GetServerDetails(request, iServer);
 		string serverName = serverDetails.GetServerName();
-		SteamNetworkingIPAddr steamNetworkingIPAddr = default(SteamNetworkingIPAddr);
+		SteamNetworkingIPAddr steamNetworkingIPAddr = default;
 		steamNetworkingIPAddr.SetIPv4(serverDetails.m_NetAdr.GetIP(), serverDetails.m_NetAdr.GetConnectionPort());
 		ServerJoinData joinData = new ServerJoinData(new ServerJoinDataDedicated(steamNetworkingIPAddr.GetIPv4(), steamNetworkingIPAddr.m_port));
 		DecodeTags(serverDetails.GetGameTags(), out var gameVersion, out var networkVersion, out var modifiers);
```
