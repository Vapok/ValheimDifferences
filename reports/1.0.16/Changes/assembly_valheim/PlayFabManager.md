# `PlayFabManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+8/-8` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PlayFabManager.cs
+++ b/PlayFabManager.cs
@@ -156,7 +156,7 @@
 		}
 		m_shouldTryAutoLogin = PlatformPrefs.GetInt("ShouldTryAutoLogin", 1) == 1;
 		instance = this;
-		UnityEngine.Object.DontDestroyOnLoad(base.gameObject);
+		UnityEngine.Object.DontDestroyOnLoad(gameObject);
 		Login();
 		Invoke("StopListeningToLogMsgs", 5f);
 	}
@@ -251,10 +251,10 @@
 			PlayFabClientAPI.UpdateUserTitleDisplayName(new UpdateUserTitleDisplayNameRequest
 			{
 				DisplayName = PlatformUserID.FilterPlatformUserID(platformUserID).m_userID
-			}, delegate(UpdateUserTitleDisplayNameResult nameResult)
+			}, (UpdateUserTitleDisplayNameResult nameResult) =>
 			{
 				ZLog.Log("Successfully set the UserTitleDisplayName to " + nameResult.DisplayName + ".");
-			}, delegate(PlayFabError error)
+			}, (PlayFabError error) =>
 			{
 				ZLog.Log("Failed to set the UserTitleDisplayName. Error: " + error?.GenerateErrorReport());
 			});
@@ -334,7 +334,7 @@
 		}
 		if (!UnifiedPopup.IsVisible() && UnifiedPopup.IsAvailable())
 		{
-			UnifiedPopup.Push(new WarningPopup("$report_user_banned_header", text, delegate
+			UnifiedPopup.Push(new WarningPopup("$report_user_banned_header", text, () =>
 			{
 				PlatformPrefs.SetInt("DontShowBannedAgain", 1);
 				UnifiedPopup.Pop();
@@ -440,7 +440,7 @@
 	private void DelayedVCRedistWarningPopup()
 	{
 		string playFabErrorBodyText = GetPlayFabErrorBodyText();
-		UnifiedPopup.Push(new WarningPopup("$playfab_couldnotloadplayfabparty_header", playFabErrorBodyText, delegate
+		UnifiedPopup.Push(new WarningPopup("$playfab_couldnotloadplayfabparty_header", playFabErrorBodyText, () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -510,7 +510,7 @@
 		PlayFabClientAPI.GetUserReadOnlyData(new GetUserDataRequest
 		{
 			PlayFabId = PlayFabUniqueId
-		}, delegate(GetUserDataResult result)
+		}, (GetUserDataResult result) =>
 		{
 			if (result.Data == null || !result.Data.ContainsKey("warning"))
 			{
@@ -518,13 +518,13 @@
 			}
 			else
 			{
-				UnifiedPopup.Push(new WarningPopup("Warning", "Another player has reported you for your online behaviour. Your actions were deemed to have breached the terms of service as listed in the EULA at valheim.com/eula. Further infractions may result in your account being banned from online play.", delegate
+				UnifiedPopup.Push(new WarningPopup("Warning", "Another player has reported you for your online behaviour. Your actions were deemed to have breached the terms of service as listed in the EULA at valheim.com/eula. Further infractions may result in your account being banned from online play.", () =>
 				{
 					PlatformPrefs.SetInt("HaveShownPlayFabWarning", 1);
 					UnifiedPopup.Pop();
 				}));
 			}
-		}, delegate(PlayFabError error)
+		}, (PlayFabError error) =>
 		{
 			ZLog.Log("Got error getting read-only user data:");
 			ZLog.Log(error.GenerateErrorReport());
```
