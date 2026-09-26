# `LocalServerList.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LocalServerList.cs
+++ b/LocalServerList.cs
@@ -1,6 +1,7 @@
 using System;
 using System.Collections.Generic;
 using System.IO;
+using NetworkingUtils;
 using Splatform;
 
 public class LocalServerList : IServerList, IDisposable
@@ -155,7 +156,7 @@
 	{
 		GetFilteredListInternal(m_tempServerList1);
 		ResolveDomainNames(m_tempServerList1);
-		ServerListUtils.UpdateServerOnlineStatus(m_tempServerList1, m_lastRefreshedTimeUtc, delegate
+		ServerListUtils.UpdateServerOnlineStatus(m_tempServerList1, m_lastRefreshedTimeUtc, (ServerData _) =>
 		{
 			ServerListUpdated?.Invoke();
 		});
@@ -169,7 +170,7 @@
 			ServerJoinData serverJoinData = servers[i];
 			if (serverJoinData.m_type == ServerJoinDataType.Dedicated && !MultiBackendMatchmaking.ServerIPAddressIsKnown(serverJoinData.Dedicated) && !m_activeDnsResolveRequests.Contains(serverJoinData.Dedicated.m_host))
 			{
-				MultiBackendMatchmaking.Instance.m_dnsResolver.ResolveDomainNameAsync(serverJoinData.Dedicated.m_host, delegate
+				MultiBackendMatchmaking.Instance.m_dnsResolver.ResolveDomainNameAsync(serverJoinData.Dedicated.m_host, (bool _, IPv6Address? _) =>
 				{
 					ServerListUpdated?.Invoke();
 				});
@@ -353,12 +354,12 @@
 			ZLog.LogWarning($"Server list save blocked because the save system session flag {SaveSystemSessionFlags.DontSaveServerList} was set");
 			return SaveStatusCode.FailedSaveDisabled;
 		}
-		SaveStatusCode num = SaveServerListToDisk(m_list);
-		if (num == SaveStatusCode.Succeess)
+		SaveStatusCode saveStatusCode = SaveServerListToDisk(m_list);
+		if (saveStatusCode == SaveStatusCode.Succeess)
 		{
 			m_wasModified = false;
 		}
-		return num;
+		return saveStatusCode;
 	}
 
 	private SaveStatusCode SaveServerListToDisk(List<ServerJoinData> list)
```
