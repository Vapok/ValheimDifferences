# `Microsoft.Xbox/Gdk.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `Assembly-CSharp.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/Microsoft.Xbox/Gdk.cs
+++ b/Microsoft.Xbox/Gdk.cs
@@ -95,7 +95,7 @@
 		if (!_initialized)
 		{
 			_initialized = true;
-			Object.DontDestroyOnLoad(base.gameObject);
+			Object.DontDestroyOnLoad(gameObject);
 			_hresultToFriendlyErrorLookup = new Dictionary<int, string>();
 			InitializeHresultToFriendlyErrorLookup();
 		}
```
