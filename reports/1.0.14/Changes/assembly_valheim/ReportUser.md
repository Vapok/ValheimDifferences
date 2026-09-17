# `ReportUser.cs` Diff (`1.0.12` $\rightarrow$ `1.0.14`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+19/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ReportUser.cs
+++ b/ReportUser.cs
@@ -173,16 +173,31 @@
 			MondayReportFailed(result.Error.Message);
 			return;
 		}
-		JObject jObject = JObject.Parse(JsonConvert.SerializeObject(result.FunctionResult));
+		string text = result.FunctionResult?.ToString();
+		if (string.IsNullOrEmpty(text))
+		{
+			MondayReportFailed("Invalid json returned!");
+			return;
+		}
+		JObject jObject;
+		try
+		{
+			jObject = JObject.Parse(text);
+		}
+		catch
+		{
+			MondayReportFailed("Invalid json returned!");
+			return;
+		}
 		if (!jObject.Value<bool>("success"))
 		{
-			string text = jObject.Value<string>("message");
-			ZLog.LogError("Monday request failed: " + text);
+			string text2 = jObject.Value<string>("message");
+			ZLog.LogError("Monday request failed: " + text2);
 			if (jObject["errors"] != null)
 			{
 				ZLog.Log(jObject["errors"].ToString());
 			}
-			MondayReportFailed(text);
+			MondayReportFailed(text2);
 		}
 		else
 		{
```
