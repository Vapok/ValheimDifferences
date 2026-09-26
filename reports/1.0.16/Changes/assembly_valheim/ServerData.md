# `ServerData.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ServerData.cs
+++ b/ServerData.cs
@@ -4,7 +4,7 @@
 
 	public readonly ServerMatchmakingData m_matchmakingData;
 
-	public static ServerData None => default(ServerData);
+	public static ServerData None => default;
 
 	public ServerData(ServerJoinData joinData)
 	{
```
