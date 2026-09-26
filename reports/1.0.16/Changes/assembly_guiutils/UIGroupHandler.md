# `UIGroupHandler.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_guiutils.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UIGroupHandler.cs
+++ b/UIGroupHandler.cs
@@ -95,7 +95,7 @@
 		{
 			return;
 		}
-		Selectable[] componentsInChildren = base.gameObject.GetComponentsInChildren<Selectable>(includeInactive: false);
+		Selectable[] componentsInChildren = gameObject.GetComponentsInChildren<Selectable>(includeInactive: false);
 		foreach (Selectable selectable in componentsInChildren)
 		{
 			if (EventSystem.current.currentSelectedGameObject == selectable.gameObject)
```
