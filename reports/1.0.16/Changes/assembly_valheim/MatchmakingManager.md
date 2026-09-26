# `MatchmakingManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MatchmakingManager.cs
+++ b/MatchmakingManager.cs
@@ -59,14 +59,14 @@
 				return;
 			}
 			m_pendingInvite = invite;
-			UnifiedPopup.Push(new YesNoPopup(header, text, delegate
+			UnifiedPopup.Push(new YesNoPopup(header, text, () =>
 			{
 				UnifiedPopup.Pop();
 				if (Menu.instance != null)
 				{
 					Menu.instance.OnLogoutYes();
 				}
-			}, delegate
+			}, () =>
 			{
 				UnifiedPopup.Pop();
 				m_pendingInvite = null;
@@ -91,12 +91,12 @@
 	{
 		if (s_instance == null)
 		{
-			invite = default(Invite);
+			invite = default;
 			return false;
 		}
 		if (!s_instance.m_pendingInvite.HasValue)
 		{
-			invite = default(Invite);
+			invite = default;
 			return false;
 		}
 		invite = s_instance.m_pendingInvite.Value;
```
