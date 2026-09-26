# `LRUCache.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/LRUCache.cs
+++ b/LRUCache.cs
@@ -19,7 +19,7 @@
 	{
 		if (!m_cache.ContainsKey(key))
 		{
-			translated = default(T);
+			translated = default;
 			return false;
 		}
 		(LinkedListNode<T>, T) tuple = m_cache[key];
```
