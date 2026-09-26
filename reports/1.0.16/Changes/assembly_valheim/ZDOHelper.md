# `ZDOHelper.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZDOHelper.cs
+++ b/ZDOHelper.cs
@@ -192,7 +192,7 @@
 	{
 		if (!container.ContainsKey(zid))
 		{
-			value = default(TType);
+			value = default;
 			return false;
 		}
 		return container[zid].TryGetValue(hash, out value);
```
