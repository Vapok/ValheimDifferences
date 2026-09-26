# `Valheim.UI/SessionPlayerListEntry.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+9/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `private void OnDestroy()`

---

## 📝 Code Diff

```diff
--- a/Valheim.UI/SessionPlayerListEntry.cs
+++ b/Valheim.UI/SessionPlayerListEntry.cs
@@ -308,6 +308,11 @@
 		}
 	}
 
+	private void OnDestroy()
+	{
+		RemoveCallbacks();
+	}
+
 	private void Update()
 	{
 		if (EventSystem.current != null && (EventSystem.current.currentSelectedGameObject == _focusPoint.gameObject || EventSystem.current.currentSelectedGameObject == _blockButton.gameObject || EventSystem.current.currentSelectedGameObject == _muteButton.gameObject || EventSystem.current.currentSelectedGameObject == _kickButton.gameObject || EventSystem.current.currentSelectedGameObject == _reportButton.gameObject || EventSystem.current.currentSelectedGameObject == _button.gameObject))
@@ -376,7 +381,7 @@
 		if (ZNet.instance != null)
 		{
 			string text = (ZNet.instance.IsServer() ? "$menu_player_list_block_warning_as_server" : "$menu_player_list_block_warning_as_client");
-			UnifiedPopup.Push(new YesNoPopup("$menu_server_warning", text, delegate
+			UnifiedPopup.Push(new YesNoPopup("$menu_server_warning", text, () =>
 			{
 				ProceedBlock(shouldLogout: true);
 			}, UnifiedPopup.Pop));
@@ -390,7 +395,7 @@
 
 	private void ProceedBlock(bool shouldLogout)
 	{
-		ZNet.PlayerInfo id = default(ZNet.PlayerInfo);
+		ZNet.PlayerInfo id = default;
 		ZNet.CrossNetworkUserInfo userInfo = new ZNet.CrossNetworkUserInfo
 		{
 			m_id = _user,
@@ -440,12 +445,12 @@
 	{
 		if (ZNet.instance != null)
 		{
-			UnifiedPopup.Push(new YesNoPopup("$menu_kick_player_title", Localization.instance.Localize("$menu_kick_player", CharacterName), delegate
+			UnifiedPopup.Push(new YesNoPopup("$menu_kick_player_title", Localization.instance.Localize("$menu_kick_player", CharacterName), () =>
 			{
 				ZNet.instance.Kick(CharacterName);
 				OnKicked?.Invoke(this);
 				UnifiedPopup.Pop();
-			}, delegate
+			}, () =>
 			{
 				UnifiedPopup.Pop();
 			}));
```
