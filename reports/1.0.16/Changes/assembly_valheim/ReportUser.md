# `ReportUser.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+7/-7` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ReportUser.cs
+++ b/ReportUser.cs
@@ -76,7 +76,7 @@
 
 	public void ClickButtonCancel()
 	{
-		Object.Destroy(base.gameObject);
+		Object.Destroy(gameObject);
 	}
 
 	public void ClickButtonSend()
@@ -94,7 +94,7 @@
 		{
 			if (m_reportedPlayfabIds.Contains(m_offenderPlayfabId))
 			{
-				UnifiedPopup.Push(new WarningPopup("$report_user_already_reported_header", "$report_user_already_reported_header", delegate
+				UnifiedPopup.Push(new WarningPopup("$report_user_already_reported_header", "$report_user_already_reported_header", () =>
 				{
 					UnifiedPopup.Pop();
 				}));
@@ -110,7 +110,7 @@
 			}
 			if (m_bodyTextInput.text.Length < 10)
 			{
-				UnifiedPopup.Push(new WarningPopup("$report_user_send_report_failed", "$report_user_send_report_cant_send_not_enough_text", delegate
+				UnifiedPopup.Push(new WarningPopup("$report_user_send_report_failed", "$report_user_send_report_cant_send_not_enough_text", () =>
 				{
 					UnifiedPopup.Pop();
 				}));
@@ -217,11 +217,11 @@
 	{
 		m_reportedPlayfabIds.Add(m_offenderPlayfabId);
 		ZLog.Log("Success! CloudScript succeeded with creating a new Monday item.");
-		UnifiedPopup.Push(new WarningPopup("$report_user_successful_header", "$report_user_successful_text", delegate
+		UnifiedPopup.Push(new WarningPopup("$report_user_successful_header", "$report_user_successful_text", () =>
 		{
 			if (this != null)
 			{
-				Object.Destroy(base.gameObject);
+				Object.Destroy(gameObject);
 			}
 			UnifiedPopup.Pop();
 		}));
@@ -236,7 +236,7 @@
 
 	private void ReportUserFailed()
 	{
-		UnifiedPopup.Push(new WarningPopup("$report_user_failed_header", "$report_user_failed_text", delegate
+		UnifiedPopup.Push(new WarningPopup("$report_user_failed_header", "$report_user_failed_text", () =>
 		{
 			UnifiedPopup.Pop();
 		}));
@@ -245,6 +245,6 @@
 
 	public bool IsReportUserWindowActive()
 	{
-		return base.gameObject.activeSelf;
+		return gameObject.activeSelf;
 	}
 }
```
