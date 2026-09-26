# `ZPlayFabMatchmaking.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+13/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZPlayFabMatchmaking.cs
+++ b/ZPlayFabMatchmaking.cs
@@ -251,7 +251,7 @@
 				Dictionary<string, string> searchData = new Dictionary<string, string> { ["string_key10"] = m_serverData.serverIp };
 				updateLobbyRequest.SearchData = searchData;
 			}
-			PlayFabMultiplayerAPI.UpdateLobby(updateLobbyRequest, delegate
+			PlayFabMultiplayerAPI.UpdateLobby(updateLobbyRequest, (LobbyEmptyResult _) =>
 			{
 				ZLog.Log($"Lobby {m_serverData.lobbyId} for world '{m_serverData.serverName}' and network {m_serverData.networkId} refreshed");
 			}, OnRefreshFailed);
@@ -260,10 +260,10 @@
 
 	private void OnRefreshFailed(PlayFabError err)
 	{
-		CreateLobby(refresh: true, delegate
+		CreateLobby(refresh: true, (CreateLobbyResult _) =>
 		{
 			ZLog.Log($"Lobby {m_serverData.lobbyId} for world '{m_serverData.serverName}' recreated");
-		}, delegate(PlayFabError playFabError)
+		}, (PlayFabError playFabError) =>
 		{
 			ZLog.LogWarning($"Failed to refresh lobby {m_serverData.lobbyId} for world '{m_serverData.serverName}': {playFabError.GenerateErrorReport()}");
 		});
@@ -394,7 +394,7 @@
 		if (m_serverData.networkId == null || m_serverData.networkId != networkId)
 		{
 			m_serverData.networkId = networkId;
-			CreateLobby(refresh: false, OnCreateLobbySuccess, delegate(PlayFabError error)
+			CreateLobby(refresh: false, OnCreateLobbySuccess, (PlayFabError error) =>
 			{
 				OnFailed("create lobby", error);
 			});
@@ -495,7 +495,7 @@
 		{
 			LobbyId = m_serverData.lobbyId,
 			SearchData = new Dictionary<string, string> { ["string_key4"] = JoinCode }
-		}, OnSetLobbyJoinCodeSuccess, delegate(PlayFabError error)
+		}, OnSetLobbyJoinCodeSuccess, (PlayFabError error) =>
 		{
 			OnFailed("set lobby join-code", error);
 		});
@@ -511,7 +511,7 @@
 		PlayFabMultiplayerAPI.FindLobbies(new FindLobbiesRequest
 		{
 			Filter = string.Format("{0} eq '{1}'", "string_key4", JoinCode)
-		}, OnCheckJoinCodeSuccess, delegate(PlayFabError error)
+		}, OnCheckJoinCodeSuccess, (PlayFabError error) =>
 		{
 			OnFailed("find lobbies", error);
 		});
@@ -554,7 +554,7 @@
 		{
 			LobbyId = m_serverData.lobbyId,
 			SearchData = new Dictionary<string, string> { ["string_key2"] = true.ToString() }
-		}, OnActivateLobbySuccess, delegate(PlayFabError error)
+		}, OnActivateLobbySuccess, (PlayFabError error) =>
 		{
 			OnFailed("activate lobby", error);
 		});
@@ -572,7 +572,7 @@
 		if (!PlayFabMultiplayerAPI.IsEntityLoggedIn())
 		{
 			ZLog.LogWarning("Calling ZPlayFabMatchmaking.RegisterServer() without logged in user");
-			m_pendingRegisterServer = delegate
+			m_pendingRegisterServer = () =>
 			{
 				RegisterServer(name, havePassword, isCommunityServer, gameVersion, modifiers, networkVersion, worldName, needServerAccount);
 			};
@@ -716,7 +716,7 @@
 		{
 			LobbyId = m_serverData.lobbyId,
 			LobbyData = lobbyData
-		}, delegate
+		}, (LobbyEmptyResult _) =>
 		{
 			ZLog.Log($"Lobby {m_serverData.lobbyId} for world '{m_serverData.serverName}' change to network {m_serverData.networkId}");
 		}, OnRefreshFailed);
@@ -728,10 +728,10 @@
 		{
 			LobbyId = lobbyId,
 			SearchData = new Dictionary<string, string> { ["string_key2"] = false.ToString() }
-		}, delegate
+		}, (LobbyEmptyResult _) =>
 		{
 			ZLog.Log("Deactivated PlayFab lobby " + lobbyId);
-		}, delegate(PlayFabError error)
+		}, (PlayFabError error) =>
 		{
 			ZLog.LogWarning($"Failed to deactive lobby '{lobbyId}': {error.GenerateErrorReport()}");
 		});
@@ -745,11 +745,11 @@
 		{
 			LobbyId = lobbyId,
 			MemberEntity = GetEntityKeyForLocalUser()
-		}, delegate
+		}, (LobbyEmptyResult _) =>
 		{
 			ZLog.Log("Left PlayFab lobby " + lobbyId);
 			LobbyLeft?.Invoke(success: true);
-		}, delegate(PlayFabError error)
+		}, (PlayFabError error) =>
 		{
 			ZLog.LogError($"Failed to leave lobby '{lobbyId}': {error.GenerateErrorReport()}");
 			LobbyLeft?.Invoke(success: false);
```
