# `ServerMatchmakingData.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ServerMatchmakingData.cs
+++ b/ServerMatchmakingData.cs
@@ -28,7 +28,7 @@
 
 	public readonly OnlineStatus m_onlineStatus;
 
-	public static ServerMatchmakingData None => default(ServerMatchmakingData);
+	public static ServerMatchmakingData None => default;
 
 	public bool IsCrossplay => !m_platformRestriction.IsValid;
 
@@ -62,12 +62,12 @@
 		m_serverName = null;
 		m_playerCount = 0u;
 		m_playerLimit = 0u;
-		m_hostUser = default(PlatformUserID);
-		m_gameVersion = default(GameVersion);
+		m_hostUser = default;
+		m_gameVersion = default;
 		m_networkVersion = 0u;
 		m_joinCode = null;
 		m_isPasswordProtected = false;
-		m_platformRestriction = default(Platform);
+		m_platformRestriction = default;
 		m_modifiers = null;
 		m_onlineStatus = ((!couldCheck) ? OnlineStatus.NotAvailable : OnlineStatus.Offline);
 	}
@@ -78,12 +78,12 @@
 		m_serverName = serverName;
 		m_playerCount = 0u;
 		m_playerLimit = 0u;
-		m_hostUser = default(PlatformUserID);
-		m_gameVersion = default(GameVersion);
+		m_hostUser = default;
+		m_gameVersion = default;
 		m_networkVersion = 0u;
 		m_joinCode = null;
 		m_isPasswordProtected = false;
-		m_platformRestriction = default(Platform);
+		m_platformRestriction = default;
 		m_modifiers = null;
 		m_onlineStatus = OnlineStatus.Offline;
 	}
```
