# `ZCursor.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_utils.dll`
* **Status**: `🟡 MODIFIED` (`+4/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ZCursor.cs
+++ b/ZCursor.cs
@@ -37,9 +37,9 @@
 
 	private static void SetRequested(bool newRequested)
 	{
-		bool num = IsRequested != newRequested;
+		bool flag = IsRequested != newRequested;
 		IsRequested = newRequested;
-		if (num)
+		if (flag)
 		{
 			IsRequestedChanged?.Invoke();
 		}
@@ -47,10 +47,10 @@
 
 	private static void SetVisible(bool newVisible)
 	{
-		bool num = newVisible != IsVisible;
+		bool flag = newVisible != IsVisible;
 		IsVisible = newVisible;
 		Cursor.visible = ZInput.IsMouseActive() && !ZInput.IsTouchActive() && !ZInput.IsGamepadMouseActive() && IsVisible;
-		if (num)
+		if (flag)
 		{
 			IsVisibleChanged?.Invoke();
 		}
```
