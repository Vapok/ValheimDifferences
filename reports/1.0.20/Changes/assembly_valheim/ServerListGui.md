# `ServerListGui.cs` Diff (`1.0.17` $\rightarrow$ `1.0.20`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `OnPlayFabJoinCodeSuccess() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/ServerListGui.cs
+++ b/ServerListGui.cs
@@ -965,7 +965,7 @@
 
 	private void OnPlayFabJoinCodeSuccess(ServerData serverData)
 	{
-		if (!serverData.m_joinData.IsValid || serverData.m_matchmakingData.m_networkVersion != 40)
+		if (!serverData.m_joinData.IsValid || serverData.m_matchmakingData.m_networkVersion != 41)
 		{
 			UnifiedPopup.Push(new WarningPopup("$menu_addserverfailed", "$error_incompatibleversion", () =>
 			{
```
