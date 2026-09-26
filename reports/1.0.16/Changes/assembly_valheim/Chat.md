# `Chat.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Chat.cs
+++ b/Chat.cs
@@ -484,7 +484,7 @@
 		}
 		if (type == Talker.Type.Shout)
 		{
-			CheckPermissionsAndSendChatMessageRPCsAsync(delegate(long user, bool filterText)
+			CheckPermissionsAndSendChatMessageRPCsAsync((long user, bool filterText) =>
 			{
 				GetChatMessageData(text, filterText, out var userInfoToSend, out var textToSend);
 				ZRoutedRpc.instance.InvokeRoutedRPC(user, "ChatMessage", Player.m_localPlayer.GetHeadPoint(), 2, userInfoToSend, textToSend);
@@ -522,7 +522,7 @@
 				{
 					continue;
 				}
-				RelationsManager.CheckPermissionAsync(playerList[i].m_userInfo.m_id, Permission.CommunicateWithUsingText, isSender: true, delegate(RelationsManagerPermissionResult result)
+				RelationsManager.CheckPermissionAsync(playerList[i].m_userInfo.m_id, Permission.CommunicateWithUsingText, isSender: true, (RelationsManagerPermissionResult result) =>
 				{
 					switch (result)
 					{
@@ -689,7 +689,7 @@
 			npcText.m_topic = topic;
 			npcText.m_text = text;
 			npcText.m_go = talker;
-			npcText.m_gui = UnityEngine.Object.Instantiate(large ? m_npcTextBaseLarge : m_npcTextBase, base.transform);
+			npcText.m_gui = UnityEngine.Object.Instantiate(large ? m_npcTextBaseLarge : m_npcTextBase, transform);
 			npcText.m_gui.SetActive(value: true);
 			npcText.m_animator = npcText.m_gui.GetComponent<Animator>();
 			npcText.m_topicField = npcText.m_gui.transform.Find("Topic").GetComponent<TextMeshProUGUI>();
```
