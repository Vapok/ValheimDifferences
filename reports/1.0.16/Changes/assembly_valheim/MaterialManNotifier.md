# `MaterialManNotifier.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/MaterialManNotifier.cs
+++ b/MaterialManNotifier.cs
@@ -4,6 +4,6 @@
 {
 	private void OnDestroy()
 	{
-		MaterialMan.instance.UnregisterRenderers(base.gameObject);
+		MaterialMan.instance.UnregisterRenderers(gameObject);
 	}
 }
```
