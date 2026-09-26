# `KeySlider.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/KeySlider.cs
+++ b/KeySlider.cs
@@ -66,7 +66,7 @@
 		{
 			SetToolTip();
 		}
-		if (ZInput.IsExclusiveGamepadActive() && EventSystem.current.currentSelectedGameObject != base.gameObject && m_lastActiveSlider == this)
+		if (ZInput.IsExclusiveGamepadActive() && EventSystem.current.currentSelectedGameObject != gameObject && m_lastActiveSlider == this)
 		{
 			m_lastActiveSlider = null;
 		}
```
