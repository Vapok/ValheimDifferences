# `PrivilegeManager.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/PrivilegeManager.cs
+++ b/PrivilegeManager.cs
@@ -64,7 +64,7 @@
 			{
 				UnifiedPopup.Pop();
 			}
-			UnifiedPopup.Push(new WarningPopup("$online_kickedfromsession_header", "$ps_online_kickedfromsession_text", delegate
+			UnifiedPopup.Push(new WarningPopup("$online_kickedfromsession_header", "$ps_online_kickedfromsession_text", () =>
 			{
 				UnifiedPopup.Pop();
 			}));
```
