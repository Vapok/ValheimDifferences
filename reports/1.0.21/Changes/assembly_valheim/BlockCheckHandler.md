# `BlockCheckHandler.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CheckForBlocked() [Method Body Modified]`
- `OnRelationsChanged() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/BlockCheckHandler.cs
+++ b/BlockCheckHandler.cs
@@ -18,8 +18,10 @@
 
 	private void OnRelationsChanged()
 	{
-		ZLog.Log("OnRelationsChanged - Calling CheckForBlocked again.");
-		CheckForBlocked(ZNet.World.m_playerHistory);
+		if (ZNet.World != null)
+		{
+			CheckForBlocked(ZNet.World.m_playerHistory);
+		}
 	}
 
 	private void CheckForBlocked(IReadOnlyList<ZNet.CrossNetworkUserInfo> historicalPlayers)
```
