# `KeyUI.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/KeyUI.cs
+++ b/KeyUI.cs
@@ -19,7 +19,7 @@
 
 	public virtual void Update()
 	{
-		if (m_lastKeyUI != this && EventSystem.current.currentSelectedGameObject == base.gameObject && ZInput.IsExclusiveGamepadActive())
+		if (m_lastKeyUI != this && EventSystem.current.currentSelectedGameObject == gameObject && ZInput.IsExclusiveGamepadActive())
 		{
 			OnPointerEnter(null);
 		}
```
