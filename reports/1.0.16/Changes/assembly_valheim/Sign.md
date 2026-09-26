# `Sign.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+12/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Sign.cs
+++ b/Sign.cs
@@ -42,8 +42,16 @@
 
 	public string GetHoverText()
 	{
-		string text = (m_isViewable ? ("\"" + GetText().RemoveRichTextTags() + "\"") : ((!m_author.HasValue || !MuteList.Instance.Contains(m_author.Value)) ? ("[" + Localization.instance.Localize("$text_hidden_notification_ugc_settings") + "]") : ("[" + Localization.instance.Localize("$text_hidden_notification_muted") + "]")));
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		string text;
+		if (m_isViewable)
+		{
+			text = "\"" + GetText().RemoveRichTextTags() + "\"";
+		}
+		else
+		{
+			text = ((!m_author.HasValue || !MuteList.Instance.Contains(m_author.Value)) ? ("[" + Localization.instance.Localize("$text_hidden_notification_ugc_settings") + "]") : ("[" + Localization.instance.Localize("$text_hidden_notification_muted") + "]"));
+		}
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return text;
 		}
@@ -67,7 +75,7 @@
 		{
 			return false;
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return false;
 		}
@@ -174,7 +182,7 @@
 
 	public void SetText(string text)
 	{
-		if (PrivateArea.CheckAccess(base.transform.position))
+		if (PrivateArea.CheckAccess(transform.position))
 		{
 			m_nview.ClaimOwnership();
 			m_nview.GetZDO().Set(ZDOVars.s_text, text);
```
