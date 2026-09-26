# `KeyToggle.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/KeyToggle.cs
+++ b/KeyToggle.cs
@@ -22,7 +22,7 @@
 	{
 		m_toggle = GetComponentInParent<Toggle>();
 		m_toggle.isOn = m_defaultOn;
-		m_toggle.onValueChanged.AddListener(delegate
+		m_toggle.onValueChanged.AddListener((bool f) =>
 		{
 			OnValueChanged();
 		});
```
