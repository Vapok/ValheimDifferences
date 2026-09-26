# `TabHandler.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/TabHandler.cs
+++ b/TabHandler.cs
@@ -65,7 +65,7 @@
 			{
 				continue;
 			}
-			tab.m_button.onClick.AddListener(delegate
+			tab.m_button.onClick.AddListener(() =>
 			{
 				OnClick(tab.m_button);
 			});
```
