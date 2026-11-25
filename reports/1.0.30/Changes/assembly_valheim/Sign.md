# `Sign.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+23/-25` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateText() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Sign.cs
+++ b/Sign.cs
@@ -103,31 +103,29 @@
 	private void UpdateText()
 	{
 		uint dataRevision = m_nview.GetZDO().DataRevision;
-		if (m_lastRevision == dataRevision)
-		{
-			UpdateViewPermission();
-			return;
-		}
-		m_lastRevision = dataRevision;
-		string currentText = m_nview.GetZDO().GetString(ZDOVars.s_text, m_defaultText);
-		m_currentText = currentText;
-		m_authorDisplayName = m_nview.GetZDO().GetString(ZDOVars.s_authorDisplayName);
-		string resolvedAuthor = m_nview.GetZDO().GetString(ZDOVars.s_author);
-		if (m_nview.IsOwner() && RelationsManager.UpdateAuthorIfHost(resolvedAuthor, ref resolvedAuthor))
-		{
-			m_nview.GetZDO().Set(ZDOVars.s_author, resolvedAuthor);
-		}
-		if (string.IsNullOrEmpty(resolvedAuthor))
-		{
-			m_author = PlatformUserID.None;
-		}
-		else if (resolvedAuthor == "host")
-		{
-			m_author = null;
-		}
-		else
-		{
-			m_author = new PlatformUserID(resolvedAuthor);
+		if (m_lastRevision != dataRevision)
+		{
+			m_lastRevision = dataRevision;
+			string currentText = m_nview.GetZDO().GetString(ZDOVars.s_text, m_defaultText);
+			m_currentText = currentText;
+			m_authorDisplayName = m_nview.GetZDO().GetString(ZDOVars.s_authorDisplayName);
+			string resolvedAuthor = m_nview.GetZDO().GetString(ZDOVars.s_author);
+			if (m_nview.IsOwner() && RelationsManager.UpdateAuthorIfHost(resolvedAuthor, ref resolvedAuthor))
+			{
+				m_nview.GetZDO().Set(ZDOVars.s_author, resolvedAuthor);
+			}
+			if (string.IsNullOrEmpty(resolvedAuthor))
+			{
+				m_author = PlatformUserID.None;
+			}
+			else if (resolvedAuthor == "host")
+			{
+				m_author = null;
+			}
+			else
+			{
+				m_author = new PlatformUserID(resolvedAuthor);
+			}
 		}
 		UpdateViewPermission();
 	}
```
