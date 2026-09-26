# `ServerJoinData.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+11/-11` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ServerJoinData.cs
+++ b/ServerJoinData.cs
@@ -13,7 +13,7 @@
 
 	private readonly ServerJoinDataDedicated m_dedicated;
 
-	public static ServerJoinData None => default(ServerJoinData);
+	public static ServerJoinData None => default;
 
 	public ServerJoinDataSteamUser SteamUser
 	{
@@ -71,8 +71,8 @@
 
 	public ServerJoinData(ServerJoinDataSteamUser steam)
 	{
-		m_playFabUser = default(ServerJoinDataPlayFabUser);
-		m_dedicated = default(ServerJoinDataDedicated);
+		m_playFabUser = default;
+		m_dedicated = default;
 		m_type = ServerJoinDataType.SteamUser;
 		m_steamUser = steam;
 		m_owner = new PlatformUserID(new Platform("Steam"), m_steamUser.m_joinUserID.m_SteamID);
@@ -80,8 +80,8 @@
 
 	public ServerJoinData(ServerJoinDataPlayFabUser playfab, PlatformUserID owner)
 	{
-		m_steamUser = default(ServerJoinDataSteamUser);
-		m_dedicated = default(ServerJoinDataDedicated);
+		m_steamUser = default;
+		m_dedicated = default;
 		m_type = ServerJoinDataType.PlayFabUser;
 		m_playFabUser = playfab;
 		m_owner = owner;
@@ -89,20 +89,20 @@
 
 	public ServerJoinData(ServerJoinDataPlayFabUser playfab)
 	{
-		m_steamUser = default(ServerJoinDataSteamUser);
-		m_dedicated = default(ServerJoinDataDedicated);
+		m_steamUser = default;
+		m_dedicated = default;
 		m_type = ServerJoinDataType.PlayFabUser;
 		m_playFabUser = playfab;
-		m_owner = default(PlatformUserID);
+		m_owner = default;
 	}
 
 	public ServerJoinData(ServerJoinDataDedicated dedicated)
 	{
-		m_steamUser = default(ServerJoinDataSteamUser);
-		m_playFabUser = default(ServerJoinDataPlayFabUser);
+		m_steamUser = default;
+		m_playFabUser = default;
 		m_type = ServerJoinDataType.Dedicated;
 		m_dedicated = dedicated;
-		m_owner = default(PlatformUserID);
+		m_owner = default;
 	}
 
 	public string GetDataName()
```
