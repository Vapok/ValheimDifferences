# `GameCamera.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateMouseCapture() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/GameCamera.cs
+++ b/GameCamera.cs
@@ -195,12 +195,12 @@
 		}
 		else if (Hud.InRadial())
 		{
-			ZCursor.LockState = ((!ZInput.IsMouseActive()) ? CursorLockMode.Locked : CursorLockMode.None);
+			ZCursor.LockState = ((!ZInput.IsMouseActive() || ZInput.IsExclusiveGamepadActive()) ? CursorLockMode.Locked : CursorLockMode.None);
 			ZCursor.Show();
 		}
 		else if (!Menu.IsVisible() || UnifiedPopup.IsVisible())
 		{
-			ZCursor.LockState = CursorLockMode.None;
+			ZCursor.LockState = (ZInput.IsExclusiveGamepadActive() ? CursorLockMode.Locked : CursorLockMode.None);
 			ZCursor.Show();
 		}
 	}
```
