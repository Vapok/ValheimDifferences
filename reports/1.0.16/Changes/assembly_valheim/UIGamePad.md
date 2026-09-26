# `UIGamePad.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/UIGamePad.cs
+++ b/UIGamePad.cs
@@ -90,7 +90,7 @@
 		if (flag && Time.frameCount - m_lastInteractFrame >= 2 && ButtonPressed())
 		{
 			m_lastInteractFrame = Time.frameCount;
-			ZLog.Log("Button pressed " + base.gameObject.name + "  frame:" + Time.frameCount);
+			ZLog.Log("Button pressed " + gameObject.name + "  frame:" + Time.frameCount);
 			if (m_button != null)
 			{
 				m_button.OnSubmit(null);
```
