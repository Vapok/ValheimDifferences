# `PlayFabManager.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+26/-13` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `CheckPlayFabWarnings() [Method Body Modified]`
- `CheckPlayFabWarnings() [Method Removed]`
- `GetBanDuration() [Method Body Modified]`
- `GetBanReason() [Method Body Modified]`
- `OnLoginFinished() [Method Body Modified]`
- `TryDisplayPlayFabWarning() [Method Body Modified]`
- `UserBannedMessageInfo() [Method Body Modified]`
- `private string GetBanReason(PlayFabError error)`
- `private void CheckPlayFabWarnings()`
- `private void TryDisplayPlayFabWarning()`

---

## 📝 Code Diff

```diff
--- a/PlayFabManager.cs
+++ b/PlayFabManager.cs
@@ -332,6 +332,7 @@
 		{
 			text += GetBanInfoBodyText(unbannedLocalTime);
 		}
+		text = text + "\n" + Localization.instance.Localize("$report_user_ban_reason", GetBanReason(error));
 		if (!UnifiedPopup.IsVisible() && UnifiedPopup.IsAvailable())
 		{
 			UnifiedPopup.Push(new WarningPopup("$report_user_banned_header", text, () =>
@@ -341,6 +342,21 @@
 			}));
 		}
 		m_accountBannedPopupShown = true;
+	}
+
+	private string GetBanReason(PlayFabError error)
+	{
+		if (error.ErrorDetails != null)
+		{
+			foreach (KeyValuePair<string, List<string>> errorDetail in error.ErrorDetails)
+			{
+				if (!string.IsNullOrEmpty(errorDetail.Key))
+				{
+					return errorDetail.Key;
+				}
+			}
+		}
+		return "";
 	}
 
 	private bool GetBanDuration(PlayFabError error, out string unbannedLocalTime)
@@ -498,12 +514,13 @@
 		{
 			PlatformPrefs.SetInt("DontShowBannedAgain", 0);
 			m_accountBanned = false;
-		}
-	}
-
-	private void CheckPlayFabWarnings()
-	{
-		if (m_accountBannedPopupShown)
+			TryDisplayPlayFabWarning();
+		}
+	}
+
+	private void TryDisplayPlayFabWarning()
+	{
+		if (PlatformPrefs.GetInt("HaveShownPlayFabWarning") == 1)
 		{
 			return;
 		}
@@ -512,13 +529,9 @@
 			PlayFabId = PlayFabUniqueId
 		}, (GetUserDataResult result) =>
 		{
-			if (result.Data == null || !result.Data.ContainsKey("warning"))
-			{
-				ZLog.Log("No warnings for this user. Carry on!");
-			}
-			else
-			{
-				UnifiedPopup.Push(new WarningPopup("Warning", "Another player has reported you for your online behaviour. Your actions were deemed to have breached the terms of service as listed in the EULA at valheim.com/eula. Further infractions may result in your account being banned from online play.", () =>
+			if (result.Data != null && result.Data.ContainsKey("warning"))
+			{
+				UnifiedPopup.Push(new WarningPopup("$menu_server_warning", "$report_user_warning_received_body", () =>
 				{
 					PlatformPrefs.SetInt("HaveShownPlayFabWarning", 1);
 					UnifiedPopup.Pop();
```
