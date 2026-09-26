# `Ledge.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Ledge.cs
+++ b/Ledge.cs
@@ -29,7 +29,7 @@
 		bool flag = false;
 		foreach (Collider item in colliders)
 		{
-			if (item.transform.position.y > base.transform.position.y)
+			if (item.transform.position.y > transform.position.y)
 			{
 				flag = true;
 				break;
```
