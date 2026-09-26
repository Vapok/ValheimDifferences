# `DisableInPlacementGhost.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/DisableInPlacementGhost.cs
+++ b/DisableInPlacementGhost.cs
@@ -9,7 +9,7 @@
 
 	private void Start()
 	{
-		if (!Player.IsPlacementGhost(base.gameObject))
+		if (!Player.IsPlacementGhost(gameObject))
 		{
 			return;
 		}
```
