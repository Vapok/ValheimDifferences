# `TeleportWorld.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TeleportWorld.cs
+++ b/TeleportWorld.cs
@@ -43,7 +43,7 @@
 		m_nview = GetComponent<ZNetView>();
 		if (m_nview.GetZDO() == null)
 		{
-			base.enabled = false;
+			enabled = false;
 			return;
 		}
 		m_hadTarget = HaveTarget();
@@ -76,7 +76,7 @@
 		{
 			return false;
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			human.Message(MessageHud.MessageType.Center, "$piece_noaccess");
 			return true;
@@ -98,7 +98,7 @@
 			bool flag = HaveTarget();
 			if (flag && !m_hadTarget)
 			{
-				m_connected.Create(base.transform.position, base.transform.rotation);
+				m_connected.Create(transform.position, transform.rotation);
 			}
 			m_hadTarget = flag;
 			bool flag2 = false;
@@ -160,7 +160,7 @@
 		ZDO zDO = m_nview.GetZDO();
 		if (zDO == null)
 		{
-			return default(TagInfo);
+			return default;
 		}
 		string text = zDO.GetString(ZDOVars.s_tagauthor);
 		PlatformUserID userId = (string.IsNullOrEmpty(text) ? PlatformUserID.None : new PlatformUserID(text));
```
