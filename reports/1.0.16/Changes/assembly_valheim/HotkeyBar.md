# `HotkeyBar.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+2/-2` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/HotkeyBar.cs
+++ b/HotkeyBar.cs
@@ -106,10 +106,10 @@
 			for (int num2 = 0; num2 < num; num2++)
 			{
 				ElementData elementData = new ElementData();
-				elementData.m_go = Object.Instantiate(m_elementPrefab, base.transform);
+				elementData.m_go = Object.Instantiate(m_elementPrefab, transform);
 				elementData.m_go.transform.localPosition = new Vector3((float)num2 * m_elementSpace, 0f, 0f);
 				int elementIndex = num2;
-				elementData.m_go.GetComponent<Button>().onClick.AddListener(delegate
+				elementData.m_go.GetComponent<Button>().onClick.AddListener(() =>
 				{
 					ElementClicked(player, elementIndex);
 				});
```
