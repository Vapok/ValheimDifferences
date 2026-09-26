# `SuspendManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/SuspendManager.cs
+++ b/SuspendManager.cs
@@ -104,7 +104,7 @@
 		if (UnifiedPopup.IsAvailable() && !UnifiedPopup.IsVisible())
 		{
 			string text = "$xbox_online_kickedfromsession_suspendresume_text";
-			UnifiedPopup.Push(new WarningPopup("$online_kickedfromsession_header", text, delegate
+			UnifiedPopup.Push(new WarningPopup("$online_kickedfromsession_header", text, () =>
 			{
 				UnifiedPopup.Pop();
 			}));
```
