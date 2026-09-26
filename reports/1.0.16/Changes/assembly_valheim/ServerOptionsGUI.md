# `ServerOptionsGUI.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+1/-1` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/ServerOptionsGUI.cs
+++ b/ServerOptionsGUI.cs
@@ -39,7 +39,7 @@
 	{
 		if (ZNet.instance != null)
 		{
-			base.gameObject.SetActive(value: false);
+			gameObject.SetActive(value: false);
 			return;
 		}
 		m_toolTipPanel.gameObject.SetActive(m_toolTipText.text.Length > 0);
```
