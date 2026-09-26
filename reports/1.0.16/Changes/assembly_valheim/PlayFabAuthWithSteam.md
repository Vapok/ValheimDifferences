# `PlayFabAuthWithSteam.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlayFabAuthWithSteam.cs
+++ b/PlayFabAuthWithSteam.cs
@@ -9,7 +9,7 @@
 
 	public static void Login()
 	{
-		SteamNetworkingIdentity serverIdentity = default(SteamNetworkingIdentity);
+		SteamNetworkingIdentity serverIdentity = default;
 		byte[] array = ZSteamMatchmaking.instance.RequestSessionTicket(ref serverIdentity);
 		if (array == null)
 		{
```
