# `VariantDialog.cs` Diff (`1.0.15` $\rightarrow$ `1.0.16`)

* **Assembly**: `assembly_valheim.dll`
* **Status**: `🟡 MODIFIED` (`+3/-3` lines)
* **Main Report**: [⬅ Back to Main Diff Report](../../Valheim_Diff.md)

---

## 📝 Code Diff

```diff
--- a/VariantDialog.cs
+++ b/VariantDialog.cs
@@ -35,7 +35,7 @@
 			(gameObject.transform as RectTransform).anchoredPosition = new Vector2((float)num2 * m_spacing, (float)(-num) * m_spacing);
 			Button component = gameObject.transform.Find("Button").GetComponent<Button>();
 			int buttonIndex = i;
-			component.onClick.AddListener(delegate
+			component.onClick.AddListener(() =>
 			{
 				OnClicked(buttonIndex);
 			});
@@ -46,13 +46,13 @@
 
 	public void OnClose()
 	{
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 	}
 
 	private void OnClicked(int index)
 	{
 		ZLog.Log("Clicked button " + index);
-		base.gameObject.SetActive(value: false);
+		gameObject.SetActive(value: false);
 		m_selected(index);
 	}
 }
```
