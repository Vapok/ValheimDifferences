# `ServerListEntryData.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ServerListEntryData.cs
+++ b/ServerListEntryData.cs
@@ -53,11 +53,11 @@
 		}
 	}
 
-	public static ServerListEntryData None => default(ServerListEntryData);
+	public static ServerListEntryData None => default;
 
 	public ServerListEntryData(ServerData serverData, string serverName = null)
 	{
-		this = default(ServerListEntryData);
+		this = default;
 		m_joinData = serverData.m_joinData;
 		m_hostUser = m_joinData.m_owner;
 		if (serverName == null)
```
