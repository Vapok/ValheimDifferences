# `VariantDialog.cs` Diff (`1.0.16` $\rightarrow$ `1.0.17`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+5/-4` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/VariantDialog.cs
+++ b/VariantDialog.cs
@@ -25,14 +25,15 @@
 			UnityEngine.Object.Destroy(element);
 		}
 		m_elements.Clear();
-		for (int i = 0; i < item.m_shared.m_variants; i++)
+		int num = Mathf.Min(item.m_shared.m_variants, item.m_shared.m_icons.Length);
+		for (int i = 0; i < num; i++)
 		{
 			Sprite sprite = item.m_shared.m_icons[i];
-			int num = i / m_gridWidth;
-			int num2 = i % m_gridWidth;
+			int num2 = i / m_gridWidth;
+			int num3 = i % m_gridWidth;
 			GameObject gameObject = UnityEngine.Object.Instantiate(m_elementPrefab, Vector3.zero, Quaternion.identity, m_listRoot);
 			gameObject.SetActive(value: true);
-			(gameObject.transform as RectTransform).anchoredPosition = new Vector2((float)num2 * m_spacing, (float)(-num) * m_spacing);
+			(gameObject.transform as RectTransform).anchoredPosition = new Vector2((float)num3 * m_spacing, (float)(-num2) * m_spacing);
 			Button component = gameObject.transform.Find("Button").GetComponent<Button>();
 			int buttonIndex = i;
 			component.onClick.AddListener(() =>
```
