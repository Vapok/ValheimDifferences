# `Talker.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Talker.cs
+++ b/Talker.cs
@@ -30,7 +30,7 @@
 	public void Say(Type type, string text)
 	{
 		ZLog.Log("Saying " + type.ToString() + "  " + text);
-		Chat.CheckPermissionsAndSendChatMessageRPCsAsync(delegate(long user, bool filterText)
+		Chat.CheckPermissionsAndSendChatMessageRPCsAsync((long user, bool filterText) =>
 		{
 			Chat.GetChatMessageData(text, filterText, out var userInfoToSend, out var textToSend);
 			m_nview.InvokeRPC(user, "Say", (int)type, userInfoToSend, textToSend);
@@ -54,10 +54,10 @@
 				num = m_shoutDistance;
 				break;
 			}
-			if (Vector3.Distance(base.transform.position, Player.m_localPlayer.transform.position) < num && (bool)Chat.instance)
+			if (Vector3.Distance(transform.position, Player.m_localPlayer.transform.position) < num && (bool)Chat.instance)
 			{
 				Vector3 headPoint = m_character.GetHeadPoint();
-				Chat.instance.OnNewChatMessage(base.gameObject, sender, headPoint, (Type)ctype, user, text);
+				Chat.instance.OnNewChatMessage(gameObject, sender, headPoint, (Type)ctype, user, text);
 			}
 		}
 	}
```
