# `BinarySearchDictionary.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/BinarySearchDictionary.cs
+++ b/BinarySearchDictionary.cs
@@ -212,7 +212,7 @@
 	{
 		if (m_length <= 0)
 		{
-			value = default(TValue);
+			value = default;
 			return false;
 		}
 		int num = BinaryFindKeyIndex(key, out var exactMatch);
@@ -221,7 +221,7 @@
 			value = m_values[num];
 			return true;
 		}
-		value = default(TValue);
+		value = default;
 		return false;
 	}
 
```
