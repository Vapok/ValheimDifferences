# `SapCollector.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SapCollector.cs
+++ b/SapCollector.cs
@@ -86,7 +86,7 @@
 		{
 			return false;
 		}
-		if (!PrivateArea.CheckAccess(base.transform.position))
+		if (!PrivateArea.CheckAccess(transform.position))
 		{
 			return true;
 		}
@@ -183,7 +183,7 @@
 	{
 		if ((bool)m_mustConnectTo && !m_root)
 		{
-			Collider[] array = Physics.OverlapSphere(base.transform.position, 0.2f);
+			Collider[] array = Physics.OverlapSphere(transform.position, 0.2f);
 			for (int i = 0; i < array.Length; i++)
 			{
 				ResourceRoot componentInParent = array[i].GetComponentInParent<ResourceRoot>();
```
