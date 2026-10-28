# `SaveSystem.cs` Diff (`1.0.20` $\rightarrow$ `1.0.21`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+6/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `ForceRefreshCache() [Method Body Modified]`
- `ForceRefreshLocalCache() [Method Body Modified]`
- `private static void InvalidateCache()`
- `public static void ForceRefreshLocalCache(SaveDataType type)`
- `public static void InvalidateCache()`

---

## 📝 Code Diff

```diff
--- a/SaveSystem.cs
+++ b/SaveSystem.cs
@@ -238,7 +238,12 @@
 		}
 	}
 
-	private static void InvalidateCache()
+	public static void ForceRefreshLocalCache(SaveDataType type)
+	{
+		s_saveCollections[type].EnsureLocalLoaded();
+	}
+
+	public static void InvalidateCache()
 	{
 		EnsureCollectionsAreCreated();
 		foreach (KeyValuePair<SaveDataType, SaveCollection> s_saveCollection in s_saveCollections)
```
