# `Menu.cs` Diff (`1.0.21` $\rightarrow$ `1.0.30`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 🔍 Identified Changes & Methods

- `UpdateCursor() [Method Body Modified]`

---

## 📝 Code Diff

```diff
--- a/Menu.cs
+++ b/Menu.cs
@@ -283,7 +283,7 @@
 	{
 		if (m_root.gameObject.activeSelf)
 		{
-			ZCursor.LockState = ((!ZInput.IsMouseActive()) ? CursorLockMode.Locked : CursorLockMode.None);
+			ZCursor.LockState = ((!ZInput.IsMouseActive() || ZInput.IsExclusiveGamepadActive()) ? CursorLockMode.Locked : CursorLockMode.None);
 			ZCursor.Show();
 		}
 	}
```
