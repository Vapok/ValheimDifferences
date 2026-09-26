# `ZPlayFabSocket.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZPlayFabSocket.cs
+++ b/ZPlayFabSocket.cs
@@ -189,7 +189,7 @@
 
 	private void InitRemotePlayer(PlayFabPlayer remotePlayer)
 	{
-		m_delayedInitActions.Add(delegate
+		m_delayedInitActions.Add(() =>
 		{
 			remotePlayer.IsMuted = true;
 			ZLog.Log("Muted PlayFab remote player " + remotePlayer.EntityKey.Id);
```
