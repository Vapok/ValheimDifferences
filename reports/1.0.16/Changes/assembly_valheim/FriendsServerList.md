# `FriendsServerList.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/FriendsServerList.cs
+++ b/FriendsServerList.cs
@@ -210,7 +210,7 @@
 				m_tempServerList.Add(m_friendsServers[i].m_joinData);
 			}
 		}
-		ServerListUtils.UpdateServerOnlineStatus(m_tempServerList, m_lastRefreshedTimeUtc, delegate
+		ServerListUtils.UpdateServerOnlineStatus(m_tempServerList, m_lastRefreshedTimeUtc, (ServerData _) =>
 		{
 			ServerListUpdated?.Invoke();
 		});
```
