# `MapTable.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MapTable.cs
+++ b/MapTable.cs
@@ -29,7 +29,7 @@
 
 	private string GetReadHoverText()
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -38,7 +38,7 @@
 
 	private string GetWriteHoverText()
 	{
-		if (!PrivateArea.CheckAccess(base.transform.position, 0f, flash: false))
+		if (!PrivateArea.CheckAccess(transform.position, 0f, flash: false))
 		{
 			return Localization.instance.Localize(m_name + "\n$piece_noaccess");
 		}
@@ -92,7 +92,7 @@
 		{
 			return false;
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -104,7 +104,7 @@
 		ZPackage mapData = GetMapData(array);
 		m_nview.InvokeRPC("MapData", mapData);
 		user.Message(MessageHud.MessageType.Center, "$msg_mapsaved");
-		m_writeEffects.Create(base.transform.position, base.transform.rotation);
+		m_writeEffects.Create(transform.position, transform.rotation);
 		return true;
 	}
 
```
