# `ZPlayFabLobbySearch.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZPlayFabLobbySearch.cs
+++ b/ZPlayFabLobbySearch.cs
@@ -83,7 +83,7 @@
 			{
 				Filter = m_searchFilters[m_currentFilter]
 			};
-			QueueAPICall(delegate
+			QueueAPICall(() =>
 			{
 				PlayFabMultiplayerAPI.FindLobbies(request, OnFindLobbySuccess, OnFindLobbyFailed);
 			});
@@ -108,7 +108,7 @@
 		{
 			ZLog.Log($"Page {m_currentPage}, {4 - m_currentPage - 1} remains: {request.Filter}");
 		}
-		QueueAPICall(delegate
+		QueueAPICall(() =>
 		{
 			PlayFabMultiplayerAPI.FindLobbies(request, OnFindServersSuccess, OnFindLobbyFailed);
 		});
@@ -181,12 +181,12 @@
 			ConnectionString = connectionString,
 			MemberEntity = ZPlayFabMatchmaking.GetEntityKeyForLocalUser()
 		};
-		QueueAPICall(delegate
-		{
-			PlayFabMultiplayerAPI.JoinLobby(request, delegate(JoinLobbyResult result)
+		QueueAPICall(() =>
+		{
+			PlayFabMultiplayerAPI.JoinLobby(request, (JoinLobbyResult result) =>
 			{
 				OnJoinLobbySuccess(result.LobbyId);
-			}, delegate(PlayFabError error)
+			}, (PlayFabError error) =>
 			{
 				OnJoinLobbyFailed(error, lobbyId);
 			});
@@ -201,7 +201,7 @@
 			{
 				LobbyId = lobbyId
 			};
-			QueueAPICall(delegate
+			QueueAPICall(() =>
 			{
 				PlayFabMultiplayerAPI.GetLobby(request, OnGetLobbySuccess, OnGetLobbyFailed);
 			});
```
