# `BlockCheckHandler.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-5` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/BlockCheckHandler.cs
+++ b/BlockCheckHandler.cs
@@ -54,12 +54,12 @@
 			m_dialogOpen = true;
 			string text = "<color=#ff0000ff>" + cnui.m_displayName + "</color>";
 			string text2 = "$blocking_joined_world_with_blocked_player " + text + " ?";
-			UnifiedPopup.Push(new YesNoPopup("$menu_server_warning", text2, delegate
+			UnifiedPopup.Push(new YesNoPopup("$menu_server_warning", text2, () =>
 			{
 				Close(notifyMultiplayerStart: true);
 				BlockList.Instance.Remove(cnui);
 				BlockList.Instance.Persist();
-			}, delegate
+			}, () =>
 			{
 				Close(notifyMultiplayerStart: false);
 				Game.instance.Logout();
@@ -80,10 +80,10 @@
 		m_dialogOpen = true;
 		string text = "<color=#ff0000ff>" + cnui.m_displayName + "</color>";
 		string text2 = "$blocking_joined_world_with_blocked_player " + text + " ?";
-		UnifiedPopup.Push(new YesNoPopup("$menu_server_warning", text2, delegate
+		UnifiedPopup.Push(new YesNoPopup("$menu_server_warning", text2, () =>
 		{
 			PlatformManager.DistributionPlatform.UIProvider.ShowUserProfile.Open(cnui.m_id);
-			PlatformManager.DistributionPlatform.UIProvider.ShowUserProfile.Closed += delegate(bool closedOk)
+			PlatformManager.DistributionPlatform.UIProvider.ShowUserProfile.Closed += (bool closedOk) =>
 			{
 				if (closedOk && RelationsManager.IsBlocked(cnui.m_id))
 				{
@@ -91,7 +91,7 @@
 				}
 				Close(notifyMultiplayerStart: true);
 			};
-		}, delegate
+		}, () =>
 		{
 			if (RelationsManager.IsBlocked(cnui.m_id))
 			{
```
